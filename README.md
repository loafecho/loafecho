# Tony Garcia

Customer ops leader who builds AI tools that people can trust. Founder of
[loafecho](https://loafecho.com).

## Selected work

- [print-compliance](https://github.com/loafecho/print-compliance):
  screens STL and 3MF files for geometry that resembles regulated weapon parts
  and returns PASS, REVIEW or BLOCK with a reason a person can check.
- [ygo-duel-agent](https://github.com/loafecho/ygo-duel-agent):
  trains a small language model to play Yu-Gi-Oh on one consumer GPU, using a
  Rust duel runner on the open-source EDOPro engine and evaluations fixed
  before each training round.
- [surface-pro7-linux-camera](https://github.com/loafecho/surface-pro7-linux-camera):
  kernel and userspace patches for the Surface Pro 7 cameras and touchscreen
  driver on Linux, with the fault-injection scripts and offline checkers used
  to test them.
- [glia-agent](https://github.com/loafecho/glia-agent):
  a maintenance agent for a Markdown notes vault that can only propose
  changes; a person approves each one and a separate executor applies it as
  one revertible commit.
- [agent-sandbox](https://github.com/loafecho/agent-sandbox):
  least-privilege microVM sandboxes for AI agents, plus a Rust tool server
  that holds risky actions until a person approves them.

## How I build

- **Checks that must be able to fail.** A test only counts if removing the
  thing it protects turns it red. glia-agent switches off each of its guards
  in turn and requires the suite to fail; the camera repo's evidence checker
  recomputes each verdict from the raw test lines instead of trusting the
  summary.
- **Approval before action.** In glia-agent and agent-sandbox the agent
  proposes or requests, a person approves, and only then does anything change.
  The rules for what an agent may never touch live in code, not in a prompt.
- **Honest limits.** Every README has a Limits section that says what was not
  tested and where the tool falls short, such as geometry that can send a file
  to review but cannot reject it, or patches tested on one device.
