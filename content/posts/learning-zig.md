+++
title = 'Learning Zig'
date = 2023-11-09T10:47:22+02:00
tags = ['zig', 'learning']
+++

Usefull commands:

### `$ zig build-exe main.zig -O awesome` ###

Compiles main.zig into awesome binary.


Snippet to play with:

```zig
// main.zig
const std = @import("std");

// This code won't compile if `main` isn't `pub` (public)
pub fn main() void {
	const user = User{
		.power = 9001,
		.name = "Goku",
	};

	std.debug.print("{s}'s power is {d}\n", .{user.name, user.power});
}

pub const User = struct {
	power: u64,
	name: []const u8,
};

```
