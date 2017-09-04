```
def matchv(vqds, cols):
    idxs, cols2, dists =[], [], []
    for vqd, col in zip(vqds, cols):
        tidx, dist= vq.vq(np.array([col]), vqd)
        idxs.append(tidx[0])
        cols2.append(vqd[tidx[0]])
        dists.append(dist[0])
    return idxs, np.asarray(cols2), dists

def encode(imgpath, vqdpath, blksize, kset):
    '''
     编码过程:
     量化图片
        |--分块
        |--得到索引
     保存索引
        |--十进制转二进制
        |--连接二进制
        |--保存成文件
    '''
    with open(vqdpath, 'rb') as f:
        vqds = pickle.load(f)
    kset = [kset]*vqds.shape[0]
    img = np.array(Image.open(imgpath))
    cols = im2col(img, blksize)
    idxs, cols2, dists = matchv(vqds, cols)
    bitstream = _int2bitstr(idxs, kset)
    hexcode = _bit2hex(bitstream)
    pack = [img.shape, hexcode]
    # make dir if result not exist
    imgdir, imgname = pth.split(imgpath)
    resdir = imgdir+pth.sep+'output'+pth.sep
    if 'output' not in os.listdir(imgdir): os.mkdir(resdir)
    lbcname = resdir + pth.splitext(imgname)[0]+'.lbc'
    with open(lbcname,'wb') as f:
        pickle.dump(pack, f)
```
