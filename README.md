<div align="center">
  <img src="resources/opencd-logo.png" width="600"/>
</div>

## Introduction
Open-CD is an open source change detection toolbox based on a series of open source general vision task tools.


## News
- 4/21/2023 - Open-CD v1.0.0 is released in [1.x branch](https://github.com/likyoo/open-cd/tree/1.x), based on OpenMMLab 2.0 ! PyTorch 2.0 is also supported ! Enjoy it !
- 3/14/2023 - Open-CD is upgraded to v0.0.3. Semantic Change Detection (SCD) is supported !
- 11/17/2022 - Open-CD is upgraded to v0.0.2, requiring a higher version of the MMSegmentation dependency.
- 9/28/2022 - The code, pre-trained models and logs of [ChangerEx](https://github.com/likyoo/open-cd/tree/main/configs/changer) are available. :yum:
- 9/20/2022 - Our paper [Changer: Feature Interaction is What You Need for Change Detection](https://arxiv.org/abs/2209.08290) is available!
- 7/30/2022 - Open-CD is publicly available!

## Benchmark and model zoo

Supported toolboxes:

- [x] [MMSegmentation](https://github.com/open-mmlab/mmsegmentation)
- [x] [pytorch-image-models](https://github.com/rwightman/pytorch-image-models)
- [ ] ...

Supported change detection model:
(_The code of some models are borrowed directly from their official repositories._)

- [x] [FC-EF (ICIP'2018)](configs/fcsn)
- [x] [FC-Siam-diff (ICIP'2018)](configs/fcsn)
- [x] [FC-Siam-conc (ICIP'2018)](configs/fcsn)
- [x] [STANet (RS'2020)](configs/stanet)
- [x] [IFN (ISPRS'2020)](configs/ifn)
- [x] [SNUNet (GRSL'2021)](configs/snunet)
- [x] [BiT (TGRS'2021)](configs/bit)
- [x] [ChangeFormer (IGARSS'22)](configs/changeformer)
- [x] [TinyCD (arXiv'2022)](configs/tinycd)
- [x] [Changer (arXiv'2022)](configs/changer)
- [x] [TinyCDv2](configs/tinycd_v2)
- [ ] ...

Supported datasets: | [Descriptions](https://github.com/wenhwu/awesome-remote-sensing-change-detection)
- [x] [LEVIR-CD](https://justchenhao.github.io/LEVIR/)
- [x] [S2Looking](https://github.com/S2Looking/Dataset)
- [x] [SVCD](https://drive.google.com/file/d/1GX656JqqOyBi_Ef0w65kDGVto-nHrNs9/edit)
- [x] [DSIFN](https://github.com/GeoZcx/A-deeply-supervised-image-fusion-network-for-change-detection-in-remote-sensing-images/tree/master/dataset)
- [x] [CLCD](https://github.com/liumency/CropLand-CD)
- [x] [RSIPAC](https://engine.piesat.cn/ai/autolearning/index.html#/dataset/detail?key=8f6c7645-e60f-42ce-9af3-2c66e95cfa27)
- [x] [SECOND](http://www.captain-whu.com/PROJECT/)
- [x] [Landsat](https://figshare.com/articles/figure/Landsat-SCD_dataset_zip/19946135/1)
- [x] [BANDON](https://github.com/fitzpchao/BANDON)
- [ ] ...

## Usage

[Docs](https://github.com/open-mmlab/mmsegmentation/tree/master/docs)

Please refer to [get_started.md](https://github.com/open-mmlab/mmsegmentation/blob/master/docs/en/get_started.md#installation) in mmseg.

#### simple usage
```
git clone https://github.com/likyoo/open-cd.git
cd open-cd
pip install -v -e .
```
train
```
python tools/train.py configs/changer/changer_ex_r18_512x512_40k_levircd.py --work-dir ./changer_r18_levir_workdir --gpu-id 0 --seed 307
```
infer
```
# get .png results
python tools/test.py configs/changer/changer_ex_r18_512x512_40k_levircd.py  changer_r18_levir_workdir/latest.pth --format-only --eval-options "imgfile_prefix=tmp_infer"
# get metrics
python tools/test.py configs/changer/changer_ex_r18_512x512_40k_levircd.py  changer_r18_levir_workdir/latest.pth --eval mFscore mIoU
```

## Citation

If you find this project useful in your research, please consider cite:

```bibtex
@article{fang2022changer,
  title={Changer: Feature Interaction is What You Need for Change Detection}, 
  author={Sheng Fang and Kaiyu Li and Zhe Li},
  year={2022},
  eprint={2209.08290},
  archivePrefix={arXiv},
  primaryClass={cs.CV}
}
```

## License

Open-CD is released under the Apache 2.0 license.

