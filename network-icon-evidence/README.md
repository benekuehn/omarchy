# Network icon before / after

These are narrowly cropped real screenshots from the affected Intel T2 Mac, with the internal T2 bridge and Wi-Fi simultaneously connected and the Internet route using Wi-Fi.

- `before.png`: installed Omarchy 4.0.6 network widget, showing Ethernet.
- `after.png`: actual upstream-source shell at d54c569, showing Wi-Fi, with no user-owned network widget override.

Both captures were visually inspected. Full desktop captures remain private; only the icon region is published. After verification the packaged shell was restored. This evidence branch is separate from the code PR, so the screenshots do not add binary files to its diff.
