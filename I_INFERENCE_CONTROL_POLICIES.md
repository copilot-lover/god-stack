# INFERENCE CONTROL & POLICIES

--------------------------------------------------------------------------------
• Reasoning levels: { none: R=0, light: 4, medium: 16, high: 32 } (cap 64).  
• Early-halt: stop if Δ‖h‖/‖h‖ < 1e-3 for ≥3 steps.  
• Routing: dynamic top-k ∈ {1,2}; capacity 0.9..1.3; strict causal.  
• Decoding: nucleus/top-p; temperature head clamps (0.95–1.05).  
• JSON constrained decoding for tool turns.  
• Formatting: ASCII fenced; tables require header + alignment row; width ≤80 enforced.  
• **Speculative decoding: DISABLED.**

--------------------------------------------------------------------------------
