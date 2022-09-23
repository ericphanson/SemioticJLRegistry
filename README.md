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
julia> ] registry add git@github.com:semiotic-ai/SemioticJLRegistry.git
```

You should now be able to add our packages using the normal Julia syntax!
For example, from the Julia REPL

```julia
julia> ] add TheGraphData
```

## Adding Your Packages To The Registry


You need to have already added the registry for this to work.
Also, make just you are in the environment of the package you want to add (starting julia with `--project` or using `activate projectpath` will both suffice).

**NOTE:** The *main* branch is protected.
If you try to register your 

### First-Time
Register your project using the `register` function from [LocalRegistry.jl](https://github.com/GunnarFarneback/LocalRegistry.jl).
As an example, here we register `TheGraphData`

```julia
julia> register(TheGraphData; registry="SemioticJLRegistry", repo="git@github.com:semiotic-ai/TheGraphData.jl.git", branch="MyRepo/v0.1.0")
```

Continue in [Creating A PR](#creating-a-pr).

### Subsequent Updates

Once you've registered your package for the first time, you can simplify the command


```julia
julia> register(TheGraphData; branch="MyRepo/v0.1.1")
```

Continue in [Creating A PR](#creating-a-pr).

### Creating A PR

Now that you've registered to a branch, create a new PR following the template.
That's it!
If you meet the [automerge requirements](https://juliaregistries.github.io/RegistryCI.jl/stable/guidelines/), you won't have to do anything more.
Else, a reviewer may contact you.

## Troubleshooting

If it's asking you for your username and password when you try to pull from or push to the registry, you probably added the registry via HTTPS, rather than SSH.
Go in *~/.julia/registries/SemioticJLRegistry* and change the *origin* to use ssh.
For security reasons, password authentication isn't allowed.
