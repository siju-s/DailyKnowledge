### Tips
1. Don't use `R.dimen.resourceId.dp` to set padding/margin on any component. The view won't appear . Example:

```
Text(
                    text = "Test", modifier = Modifier
                        .wrapContentHeight()
                        .align(Alignment.End)
                        .padding(R.dimen.padding_5.dp)
                )

```
Here, calling `padding_5.dp` wont work 