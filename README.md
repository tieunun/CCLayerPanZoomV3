CCLayerPanZoomV3
================

An implementation of CCLayerPanZoom for Cocos2d v3. 


Swift example for tiled maps.

1. Add the source files to your project and import them using your bridging header.

        override init() {
            map = CCTiledMap(file: "world2.tmx")
            map.anchorPoint = CGPoint(x:0, y:0)
            

            panZoomLayer = CCLayerPanZoom();
            
            var winSize:CGSize = CCDirector.sharedDirector().view.frame.size;
            var boundingRect:CGRect = CGRectMake(0, 0, 0, 0);
            boundingRect.size = map.boundingBox().size;
            
            super.init()
            panZoomLayer.mode = kCCLayerPanZoomModeSheet;
            panZoomLayer.rubberEffectRatio = 0.0;
            panZoomLayer.addChild(map);
            panZoomLayer.delegate = self;
            panZoomLayer.contentSize = boundingRect.size;
            panZoomLayer.anchorPoint = CGPointMake(0.5, 0.5);
            panZoomLayer.position = CGPointMake(0.5 * winSize.width, 0.5 * winSize.height);
            panZoomLayer.panBoundsRect = CGRectMake(0, 0, winSize.width, winSize.height);
            panZoomLayer.minScale = 0.2;
            panZoomLayer.maxScale = 2.0
            panZoomLayer.scale = 0.1
        
            
            self.addChild(panZoomLayer , z:1);
        }
