# SemioticJLRegistry

A registry for Semiotic's Julia packages.

## Using Packages From The Registry

1. Use system git rather than libgit2

```bash
export JULIA_PKG_USE_CLI_GIT=true
```

Or, on fish

```fish
set -xg JULIA_PKG_USE_CLI_GIT true
```

2. From the Julia REPL

```julia
julia> ] registry add https://github.com/semiotic-ai/SemioticJLRegistry
```

You should now be able to add our packages using the normal Julia syntax!
For example, from the Julia REPL

```julia
julia> ] add TheGraphData
```

## Adding Your Packages To The Registry

Register your project using the `register` function from [LocalRegistry.jl](https://github.com/GunnarFarneback/LocalRegistry.jl).
As an example, here we register `TheGraphData`

```julia
julia> register(TheGraphData; registry="SemioticJLRegistry", repo="git@github.com:semiotic-ai/TheGraphData.jl.git")
```

You need to have already added the registry for this to work.
Also, make just you are in the environment of the package you want to add (starting julia with `--project` or using `activate projectpath` will both suffice).
