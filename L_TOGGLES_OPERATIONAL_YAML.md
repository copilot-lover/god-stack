# TOGGLES (OPERATIONAL YAML)

--------------------------------------------------------------------------------
deepnorm:
  enabled: true
  arch: decoder_only
  r_max: 32                 # choose 16 or 32; recompute alpha/beta if changed
  alpha: 4.08               # (2M)^(1/4) with M from r_max
  beta: 0.17                # (8M)^(-1/4)
  scaled_params: [ffn, attn.v_proj, attn.out_proj]
  unscaled_params: [attn.q_proj, attn.k_proj, router]

switchall:
  enabled: true
moepp:                      # MoE++ (moe plus plus)
  enabled: true
  top_k: [1,2]
  capacity_range: [0.9, 1.3]
  load_balance: bias_based
  gate_entropy_reg: 0.01
  zero_copy_experts: true

aunet:
  stages: 3
  stage0: {d_model: 384, layers: 4, aux_loss_w: 0.05}
  stage1: {d_model: 768, layers: 6, pool_len_min: 2, pool_len_max: 16, aux_loss_w: 0.10}
  stage2:
    d_model: 1536
    prelude_layers: 6
    core_layers_shared: 4
    coda_layers: 4
    recurrent:
      enabled: true
      train:
        tbptt_K: 6
        unroll_dist: lognormal_poisson
      infer:
        levels: {none: 0, light: 4, medium: 16, high: 32}
        max_R: 64
        early_halt: {delta_norm_eps: 1.0e-3, hold_steps: 3}
    mtp_heads: 4
    mtp_loss_weights: [1.0, 0.7, 0.5, 0.3]

experts:
  attention: [attn_compression, short_context, visual_understanding]
  ffn: [knowledge, math, writing, tool_calling, web_search, visual_formatting]
  active: [knowledge, math, writing, tool_calling, web_search, visual_formatting, visual_understanding, attn_compression, short_context]

precision:
  attn_compute: int4xint4_to_fp16
  softmax: fp16
  head_fallback: fp8
  ffn_compute: int4_to_fp16
  fp8_training:
    enabled: true
    activations: E4M3
    weights: E5M2
    scaling: {granularity: block_or_channel, dynamic: true}
    sensitive_ops_fp16: [recurrent_accum, norms, router_logits]

kv_cache:
  bits: 3
  per_head_channel_scales: true
  paging: {enabled: true, page_units: 16384}

context:
  primary_units: 65536
  scaling: {compression: true, alibi_yarn: true, retrieval: true}

runtime:
  flash_attention: {autotune: false, enable_if_attention_share_gt: 0.40}
  speculative_decoding: disabled

decoding:
  strategy: top_p
  temperature_head: {min: 0.95, max: 1.05}
  json_constrained_for_tools: true

--------------------------------------------------------------------------------
