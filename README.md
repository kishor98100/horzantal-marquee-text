# horizantal-marquee-view
> A react-native horizantal  marquee text component.

If you need a vertical marquee text, please use [vertical-marquee-view](https://github.com/kishor98100/vertical-marquee-view).



## Anchors

1. [Desc](#desc)
2. [Install](#install)
3. [Usage](#usage)
4. [Props](#props)
5. [Update Log](#update-log)


## Desc

[Skip this part, go to **#Install**](#install)

I needed a marquee text in one of my recent project and I didn't find a good one online, so I decided to create my own marquee text component.

I intended to make it work well on both iOS and Android, still there remains one thing in iOS which I cannot fix. I found that in **iOS**, when you use `View` component to wrap child components and don't explicitly set the parent `View` component width (e.g. use `flex`), the parent `View` component will have the same width as it's child. 

It becomes a problem in this custom component because I use a child `View` component to wrap `Text` component in order to make the text expand and show in one line. I **set the text containner `View` component size to be bigger than the `Text` so that it will not have multiple lines nor have the overflow text replaced by ellipsis.** The default value of text container width is 1000, which is usually larger than the actual label width. This results in the problem mentioned above, the wrapper `View` width becomes 1000 also.

```js
<View class="marquee-label">
  <View class="marquee-label-text-container">
    <Text class="marquee-label-text">{text}</Text>
  </View>
</View>
```

**Note:**

- In Andorid, you can use both `width` or `flex` to layout the view.
- In iOS, use `width` to layout the view. `flex` layout is not supported.


## Install

```sh
npm install --save horizantal-marquee-view
```

## Usage

1. Import

```js
import HorizantalMarqueeText from 'horizantal-marquee-view';
```

2. Use

```js
<HorizantalMarqueeText
  duration={8000}
  text={'This is a Marquee Label.'}
  textStyle={{ fontSize: 13, color: 'white' }}
/>
```

or

```js
<HorizantalMarqueeText
  speed={250}
  textStyle={{ fontSize: 13, color: 'white' }}
>
  This is a Marquee Label.
</HorizantalMarqueeText>
```

## Props

- `children`: string, the text to show in the marquee. Alternative to `text`.
- `text`: string, the text to show in the marquee. Alternative to `children`.
- `duration`: number(unit: millisecond), the duration for the marquee to run one round. e.g. 6000 (for 6 seconds a round). Alternative to `speed`.
- `speed`: number(unit: px/s, px per second), the speed of the marquee. Alternative to `duration`.
- `bgViewStyle`: stylesheet object, background view component custom styles.
- `textStyle`: stylesheet object, text component custom styles.
- `textContainerWidth`: number, text container component width. If the text is not shown in one line, increase this value.
- `textContainerHeight`: number, text container component height. If the text is not shown in one line, increase this value.
- `textContainerStyle`: stylesheet object, not recommended to use, text containner component custom style.

## Update Log

### 2019.08.16 `Version 1.0.0`

- Dynamic Text Support: now you can use dynamic text with this component :D
