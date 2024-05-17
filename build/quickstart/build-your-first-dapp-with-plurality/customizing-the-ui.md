# Customizing the UI

To change the look and feel of the Social Connect button to better match your dApp's UI, you can use the following customization attributes:

### Customizable attributes

* `height`: Specify the height of the button
* `width`: Specify the width of the button
* `initialBackgroundColor`: Specify the intial background color of the button
* `initialTextColor`: Specify the intial text color of the button
* `flipBackgroundColor`: Specify the flipped background color of the button
* `flipTextColor`: Specify the flipped text color of the button

In practice, it would look something like this:

```
<PluralitySocialConnect
    ...
    customization={{ height: '200px', width: '500px', initialBackgroundColor: '#E8A123', initialTextColor: '#FFFFFF', flipBackgroundColor: '#12AE83', flipTextColor: '#FFFFFF'}}
    ...
/>
```
