`torch.repeat_interleave(input, repeats, dim=None, *, output_size=None) -> Tensor`
- repeat elements of a tensor.

**Warning**
- This is different from `torch.Tensor.repeat()` but similar to `numpy.repeat`.

**Parameters**
- **input** ([[torch.tensor]]) - the input tensor
- **repeats** ([[torch.tensor]] or [[int]]) - The number of repetitions for each element. repeats is broadcasted to fit the shape of the given axis.
- **dim** ([[int]], optional) - The dimension along which to repeat values. By default, use the flattened input array, and return a flat output array. 

**Keyword Arguments**
- **output_size** ([[int]], optional) - Total output size for the given axis (e.g. sum of repeats). If given, it will avoid stream synchronization needed to calculate output shape of the tensor.

**Returns**
- Repeated tensor which has the same shape as input, except along the given axis.

**Return type**
* [[torch.tensor]]

**Example**
```python
>>> x = torch.tensor([1, 2, 3])
>>> x.repeat_interleave(2)
tensor([1, 1, 2, 2, 3, 3])
>>> y = torch.tensor([[1, 2], [3, 4]])
>>> torch.repeat_interleave(y, 2)
tensor([1, 1, 2, 2, 3, 3, 4, 4])
>>> torch.repeat_interleave(y, 3, dim=1)
tensor([[1, 1, 1, 2, 2, 2],
        [3, 3, 3, 4, 4, 4]])
>>> torch.repeat_interleave(y, torch.tensor([1, 2]), dim=0)
tensor([[1, 2],
        [3, 4],
        [3, 4]])
>>> torch.repeat_interleave(y, torch.tensor([1, 2]), dim=0, output_size=3)
tensor([[1, 2],
        [3, 4],
        [3, 4]])
```

used in **diffuers.pipelines.controlnet.pipeline_controlnet.StableDiffusionControlNetPipeline** function **prepare_image**.
```python
def prepare_image(
self,
image,
width,
height,
batch_size,
num_images_per_prompt,
device,
dtype,
do_classifier_free_guidance=False,
guess_mode=False,
):

	image = self.control_image_processor.preprocess(image, height=height, width=width).to(dtype=torch.float32)
	
	image_batch_size = image.shape[0]
	
	if image_batch_size == 1:
		repeat_by = batch_size
	else:
		# image batch size is the same as prompt batch size
		repeat_by = num_images_per_prompt
	
	image = image.repeat_interleave(repeat_by, dim=0) # return Tensor
	
	image = image.to(device=device, dtype=dtype)
	
	if do_classifier_free_guidance and not guess_mode:
		image = torch.cat([image] * 2)
	
	  
	
		return image
```
