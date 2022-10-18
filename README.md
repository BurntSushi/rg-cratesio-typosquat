This is the [`rg` crate][rgcrate] that always fails to compile and suggests
that folks run `cargo install ripgrep` instead. Namely, while `rg` is the
command name of ripgrep, `ripgrep` is the proper crate name.

Note that if you did run `cargo install rg`, then since it results in a
compilation error, there is no need to uninstall the `rg` crate first.

## FAQ

### Why not make `cargo install rg` just install ripgrep?

Having two different but slightly similar crate names install the same tool
leads to auditing challenges and confusion. For example, if someone sees `cargo
install rg` in an installation script, but notes that ripgrep's README suggests
`cargo install ripgrep`, they might rightfully wonder whether they're
installing the right thing or not. ripgrep could note this in the README, but
such subtle details are easy to miss.

It's better to keep it simple and prevent the `rg` crate from ever doing
anything but failing and telling folks that `ripgrep` is what they want.

### Doesn't this just encourage crates.io squatting?

I admit that it's possible that it does, but I personally believe this
particular case is worth it. Of all the crates I maintain, this is the only
example of a crate I've squatted to try and prevent user installation errors.
I believe this case to be worth it, given that `rg` is the name of ripgrep's
command itself, and `rg` is otherwise not necessarily a desirable name unto
itself.

I will happily comply with any requests from the crates.io team or any policy
changes that make this sort of thing disallowed.

But in general, no, I do not recommend going out and trying to squat every
possible synonym or typo of your crate name.

[rgcrate]: https://crates.io/crates/rg
