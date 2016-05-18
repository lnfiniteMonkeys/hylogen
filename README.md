# [*H Y L O G E N*](https://hylogen.com)  
[![Hackage Status](https://img.shields.io/hackage/v/hylogen.svg)](https://hackage.haskell.org/package/hylogen)

![](data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==)

Hylogen is a purely functional language [embedded in Haskell](https://wiki.haskell.org/Embedded_domain_specific_language) for live-coding fragment shaders, featuring:

- a simple and pure syntax
- standard operators (`+`, `*`, [`*^`,  `<.>`](https://hackage.haskell.org/package/vector-space))
- compat. w/ your fav haskell goodies (higher-order functions, ADTS, swanky polymorphism).

![](data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==)

It comes with `hyde`, an accompanying rendering environment featuring:
- *hot-reloading*
- audio-reactive primitives
- texture backbuffering

![](data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==)


## Install
```
cabal update
cabal install hylogen
```

This will install the hylogen package and `hyde`, the rendering environment.

![](data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==)

## Usage

```haskell
-- ./Main.hs
module Main where
import Hylogen.WithHyde

color = vec4 (a, a, a, 1)
  where
    a = cos(uvN !X * sin(time / 10) * 10 + mouse !X)
      + sin(uvN !Y * sin(time / 10) * 10 + mouse !Y)

main = putStrLn . toGLSL $ color
```

#### 1. run hyde...

```
hyde Main.hs
```

#### 2. ... live-code!
Go to [localhost:5678](http://localhost:5678) in your browser.

You will now see your changes to `Main.hs` propagate to your WebGL rendering environment!

![](data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==)

## References
- [The_Force](https://github.com/shawnlawson/The_Force) by Shawn Lawson. Live-coding audio-reactive shaders!
- [Type-Safe Observable Sharing](https://pdfs.semanticscholar.org/4838/bd0a91b3058b467fa31ad9e0810121b46388.pdf) by Andy Gill. [`data-reify`](https://hackage.haskell.org/package/data-reify) made compile times combinatorially faster!

## Resources
- [hackage](https://hackage.haskell.org/package/hylogen)

- [examples](https://github.com/sleexyz/hylogen-yay)
