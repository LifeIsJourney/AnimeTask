# AnimeTask

Task Animation Library for Unity

![gif_animation_001](https://user-images.githubusercontent.com/961165/85936316-77f1e180-b934-11ea-9614-9d1aa152bd41.gif)

## Instructions

- Import [UniTask](https://github.com/Cysharp)
- Import AnimeTask
    - Package Manager `git@github.com/kyubuns/AnimeTask.git?path=Assets/AnimeTask`
        - UniTask must also be installed by PackageManager
    - [UnityPackage](https://github.com/kyubuns/AnimeTask/releases)
        - AnimeTask.asmdef must have a reference to UniTask.
        - <img width="300" alt="Screen Shot 2020-06-27 at 22 48 21" src="https://user-images.githubusercontent.com/961165/85923709-51965c80-b8c8-11ea-8c3a-f0b321d0d4ab.png">

## Sample

### Basic

`(-5f, 0f, 0f)` から `(5f, 0f, 0f)` へ2秒かけて移動する。

```csharp
await Anime.Play(
    Easing.Create<Linear>(new Vector3(-5f, 0f, 0f), new Vector3(5f, 0f, 0f), 2f),
    TranslateTo.LocalPosition(cube)
);
```

### PlayTo

PlayToを利用すると、現在地から移動する。

```csharp
await Anime.PlayTo(
    Easing.Create<Linear>(new Vector3(-5f, 3f, 0f), 2f),
    TranslateTo.LocalPosition(cube)
);
```

### Easing

EasingのInCubicを利用して移動する。

```csharp
await Anime.PlayTo(
    Easing.Create<InCubic>(new Vector3(-5f, 3f, 0f), 2f),
    TranslateTo.LocalPosition(cube)
);
```

### Linear

秒速1で、2秒間移動する。

```csharp
await Anime.PlayTo(
    Moving.Linear(1f, 2f),
    TranslateTo.LocalPositionX(cube)
);
```

### Gravity

```csharp
const float xRange = 5f;
const float yRangeMin = 5f;
const float yRangeMax = 10f;
await Anime.PlayTo(
    Moving.Gravity(
        new Vector3(Random.Range(-xRange, xRange), Random.Range(yRangeMin, yRangeMax)),
        Vector3.down * 9.8f,
        5f),
    TranslateTo.LocalPosition(shape)
);
```

### TranslateTo.Action

TranslateTo.Actionを利用すると、アニメーションした値を自由に使用出来る。

```csharp
await Anime.Play(
    Easing.Create<Linear>(0, 100, 2f),
    TranslateTo.Action<float>(x => Debug.Log(x))
);
```

## Requirements

- Requires Unity2018.4 or later

## License

MIT License (see [LICENSE](LICENSE))

