# Nix sandbox

This project is a sandbox for Nix development.
Additionally, some Nix resources are also listed here.

## Resources

The following resources might be useful when writing Nix:

- <https://nixos.org/manual/nix/unstable/introduction.html>
- <https://teu5us.github.io/nix-lib.html>
- <https://fasterthanli.me/series/building-a-rust-service-with-nix/part-10>

Useful projects:

- <https://github.com/numtide/flake-utils>
- <https://github.com/DeterminateSystems/zero-to-nix>

## Tools

### Hash for `fetchgit`

Nix `pkgs.fetchgit` requires a sha256 hash. The best way to obtain this hash is by using the `nix-prefetch-git` command and provide the link and git ref (e.g. commit hash or tag) as arguments. For example:

```sh
nix-prefetch-git https://gitlab.com/duke-artiq/dax.git v6.7
```

See the Nix environment below.

```nix
{ pkgs ? import <nixpkgs> { } }:

pkgs.mkShell {
  buildInputs = [
    pkgs.nix-prefetch-git
  ];
}
```

### Cache

Potential alternatives for a Nix cache (instead of Hydra) are:

- <https://nixos.wiki/wiki/Binary_Cache>
- <https://github.com/helsinki-systems/harmonia>
- <https://www.cachix.org/>
- <https://github.com/edolstra/nix-serve>
