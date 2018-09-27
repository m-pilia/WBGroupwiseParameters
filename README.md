# Elastix configuration

```
(FixedInternalImagePixelType "short")
(MovingInternalImagePixelType "short")
(FixedImageDimension 4)
(MovingImageDimension 4)
(UseDirectionCosines "true")

(Registration "MultiMetricMultiResolutionRegistration")
(Interpolator "ReducedDimensionBSplineInterpolator" "ReducedDimensionBSplineInterpolator" "ReducedDimensionBSplineInterpolator")
(ResampleInterpolator "FinalReducedDimensionBSplineInterpolator" "FinalReducedDimensionBSplineInterpolator" "FinalReducedDimensionBSplineInterpolator")
(Resampler "DefaultResampler")
(BSplineInterpolationOrder 1)
(BSplineTransformSplineOrder 3)
(FinalBSplineInterpolationOrder 3)
(FixedImagePyramid "FixedRecursiveImagePyramid" "FixedRecursiveImagePyramid" "FixedRecursiveImagePyramid")
(MovingImagePyramid "MovingRecursiveImagePyramid" "MovingRecursiveImagePyramid" "MovingRecursiveImagePyramid")
(Transform "BSplineStackTransform")
(HowToCombineTransforms "Compose")

(Optimizer "AdaptiveStochasticGradientDescent")
(ASGDParameterEstimationMethod "DisplacementDistribution")
(NumberOfSpatialSamples 10000)
(NewSamplesEveryIteration "true")
(ImageSampler "RandomCoordinate" "RandomCoordinate" "RandomCoordinate")
(MaximumNumberOfSamplingAttempts 10)
(CheckNumberOfSamples "true")

(FinalGridSpacingInPhysicalUnits 16)

(Metric "VarianceOverLastDimensionMetric" "VarianceOverLastDimensionMetric" "VarianceOverLastDimensionMetric")

(Metric0Weight  1.00)
(Metric1Weight  1.00)
(Metric2Weight 10.00)

(SubtractMean "true")
(MovingImageDerivativeScales 1 1 1 0)

(ErodeMask "false")
(ErodeFixedMask "false")
(ErodeMovingMask "false")

(NumberOfResolutions 5)
(ImagePyramidSchedule 16 16 16 0   8 8 8 0   4 4 4 0   2 2 2 0   1 1 1 0)
(MaximumNumberOfIterations 2000 2000 2000 3000 4000)

(DefaultPixelValue 0)
(WriteResultImage "true")
(ResultImagePixelType "short")
(ResultImageFormat "nii")
```

# Command

```bash
$elastix \
	-fMask $mask \
	\
	-f0 $fat \
	-f1 $wat \
	-f2 $mask \
	\
	-m0 $fat \
	-m1 $wat \
	-m2 $mask \
	\
	-p $params \
	-out $out
```

Where `$fat`/`$wat`/`$mask` represent the location of the fat/water/mask 4D
volumes containing the moving images, `$params` is the location of the
parameter file, and `$out` is the location of a folder for the output.

