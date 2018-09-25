Always confused with the numpy append function, what's different between append and concatenate?

I found it's easy, so easy.
np.append(a,b,axis)
shape of a and b are same exclude the 'axis' axis
so in 'axis' axis, a and b are concatenated
and np.append(a,b,axis) is implemented by np.concatenated(a, b, axis), just checked before concatenated if the axis is None, 
if it is, flatten it and concatenate.

```python
def append(arr, values, axis=None):
    arr = asanyarray(arr)
    if axis is None:
        if arr.ndim != 1:
            arr = arr.ravel()
        values = ravel(values)
        axis = arr.ndim-1
    return concatenate((arr, values), axis=axis)
```
