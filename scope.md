# Loftr-hap

This is a repo where we will experiment with fine-tuning of [LoFTR](https://github.com/zju3dv/LoFTR) specifically for our purposes.

Our use-case:
- Matching historical aerial photographs (HAP) to modern reference images. 
- Both are provided as rasters
- The GSD varies somewhat between the reference and the target image as it is never possible to precisely match these in advance.
- Some HAP are greyscale 
- HAP frames can be very large images. 

## Prior learning

These are my annecdotal observations. They are tentative and not supported by data. You can challenge these if you're willing to
 
From using the pre-trained outdoor version of LofTR in the past I have found that: 
- The outdoor version of LofTR works better than indoor 
- The longer the temporal separation between the two images to be matched, the fewer the tie points that LofTR will find.
- Much of the above is driven by real changes to the landscape. Especially where urban development or major infrastructure projects have been undertaken. It may not be possible for LoFTR to match images in these cases.
- Seasonal and weather difference can also drive the mis-match such as snow or cloud cover or water levels in lakes. It may not be possible for LoFTR to match images in these cases.
- ~2m GSD is sufficient resolution to find tie-points.
- LoFTR does not perform well at coarse GSDs (>10m) 

## Training data

Your first job is to identify a suitable training dataset. There is circularity in using [our own LoFTR matched mosaics](https://hapmap.app/browse/#/) but I would be interested if the fine-tune would nevertheless improve performance in some ways.

## Testing data

All tests are conducted with testing data that is not part of the training set. 

## Goal

Your goal is to fine-tune LoFTR so that it performs better for our use-case:
1. Build a training dataset. 
2. Create and test an environemnt for fine-tuning LoFTR on hectar's GPU
3. Create quantitative tests to evaluate the performance of new LoFTR models within our domain. 
4. Fine-tune LoFTR on your dataset and test its performance within our domain compared to the generic pre-trained LoFTR.
5. iterate fine-tuning trying to improve the score until you are satisfied that you have found the best data and method.
5. Show Bilby the results comparing your fine-tuned LoFTR to the generic version.
5. Iterate by idetifying potential strategies for splitting the problem into sub-problems (large time spans, coarse GSDs etc).
5. Show Bilby the results comparing your best fine-tuned LoFTR models to the generic version and the all-purpose domain version created in step.

The best model is the one that reliably finds a coherent set of tie-points between nadir aerial images of the same location regardless of the time separating the two photos or the quality of the historical image. A good solution also minimises false positives where images that are not of the same place are matched. 

