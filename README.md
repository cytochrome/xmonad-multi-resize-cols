MultiResizableColumns
========================



MultiResizableColumns is Layout Module of XMonad.which has features of MultiColumns and ResizableTiles.



heres my configuration-file (-xmonad.hs-) as Usage/Examples

---

## xmonad.hs

---
    -- ...
    -- ...
    -- ...

    import XMonad.Layout.MultiResizableColumns

    -- ...
    -- ...
    -- ...


    ------------------------------------------------------------------------
    -- Key bindings. Add, modify or remove key bindings here.
    --
    myKeys conf@(XConfig {XMonad.modMask = modm}) = M.fromList $
     
    -- ...
    -- ...
    -- ...
    -- ...

        -- in MultiResisableColumns 
        -- Shrink/Expand:        Shrink/Expand the width  of column
        -- Shrink/ExpandMirror:  Shrink/Expand the height of column
     
        , ((modm .|. myMod3Mask, xK_h    ), sendMessage Shrink )
        , ((modm .|. myMod3Mask, xK_l    ), sendMessage Expand )
        , ((modm .|. myMod3Mask, xK_j    ), sendMessage ShrinkMirror )
        , ((modm .|. myMod3Mask, xK_k    ), sendMessage ExpandMirror )

    -- ...
    -- ...
    -- ...
    -- ...

    -- myLayout
    myLayout = spacing 4 ( Full ||| vSplitMRC  )
        where
          vSplitMRC = renamed [Replace "| vSplit |"] $ mrc
            where mrc = multiResizableColumns [2,2] (5/100) (replicate 3 (0.33,[0.33,0.33,0.33])) 3



