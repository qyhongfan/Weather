# Weather
墨迹天气，天气预报，动态天气，天气Animation



[GitHub: https://github.com/Zws-China/Weather](https://github.com/Zws-China/Weather)  


# PhotoShoot
![image](https://github.com/Zws-China/.../blob/master/Weather.gif)<br>
![image](https://github.com/Zws-China/.../blob/master/suny.gif)
![image](https://github.com/Zws-China/.../blob/master/cloud.gif)<br>
![image](https://github.com/Zws-China/.../blob/master/rain.gif)
![这里写图片描述](http://img.blog.csdn.net/20170407173624997?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMjY1OTgwNzc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)<br>

# How To Use

```ruby


//动画横向移动方法（云、鸟移动）
- (CABasicAnimation *)birdFlyAnimationWithToValue:(NSNumber *)toValue duration:(NSInteger)duration{
    CABasicAnimation *animation = [CABasicAnimation animationWithKeyPath:@"transform.translation.x"];
    animation.toValue = toValue;
    animation.duration = duration;
    animation.removedOnCompletion = NO;
    animation.repeatCount = MAXFLOAT;
    animation.fillMode = kCAFillModeForwards;
    return animation;
}

//动画旋转方法，（阳光旋转、雪花旋转）
- (CABasicAnimation *)sunshineAnimationWithDuration:(NSInteger)duration{
    //旋转动画
    CABasicAnimation* rotationAnimation = [CABasicAnimation animationWithKeyPath:@"transform.rotation.z"];
    rotationAnimation.toValue = [NSNumber numberWithFloat: M_PI * 2.0 ];
    [CAMediaTimingFunction functionWithName:kCAMediaTimingFunctionEaseInEaseOut];
    rotationAnimation.duration = duration;
    rotationAnimation.repeatCount = MAXFLOAT;//你可以设置到最大的整数值
    rotationAnimation.cumulative = NO;
    rotationAnimation.removedOnCompletion = NO;
    rotationAnimation.fillMode = kCAFillModeForwards;
    return rotationAnimation;
}

//下雨、下雪动画方法
- (CABasicAnimation *)rainAnimationWithDuration:(NSInteger)duration{

    CABasicAnimation* caBaseTransform = [CABasicAnimation animation];
    caBaseTransform.duration = duration;
    caBaseTransform.keyPath = @"transform";
    caBaseTransform.repeatCount = MAXFLOAT;
    caBaseTransform.removedOnCompletion = NO;
    caBaseTransform.fillMode = kCAFillModeForwards;
    caBaseTransform.fromValue = [NSValue valueWithCATransform3D:CATransform3DMakeTranslation(-170, -620, 0)];
    caBaseTransform.toValue = [NSValue valueWithCATransform3D:CATransform3DMakeTranslation(kScreenHeight/2.0*34/124.0, kScreenHeight/2, 0)];

    return caBaseTransform;

}
//透明度动画
- (CABasicAnimation *)rainAlphaWithDuration:(NSInteger)duration {

    CABasicAnimation *showViewAnn = [CABasicAnimation animationWithKeyPath:@"opacity"];
    showViewAnn.fromValue = [NSNumber numberWithFloat:1.0];
    showViewAnn.toValue = [NSNumber numberWithFloat:0.1];
    showViewAnn.duration = duration;
    showViewAnn.repeatCount = MAXFLOAT;
    showViewAnn.fillMode = kCAFillModeForwards;
    showViewAnn.timingFunction = [CAMediaTimingFunction functionWithName:kCAMediaTimingFunctionEaseInEaseOut];
    showViewAnn.removedOnCompletion = NO;

    return showViewAnn;
}


```