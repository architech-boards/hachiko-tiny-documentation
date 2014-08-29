To deploy the root file system, you are going to need an USB flash drive.

.. warning::

 The USB flash drive content will be lost forever!

1. Umount the device:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'deploy_rootfs_rst-host-141' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="deploy_rootfs_rst-host-141" class="language-markup">sudo umount /path/to/your/USB/device/partition</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

2. Align a new partition to the first sector of your USB device:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'deploy_rootfs_rst-host-142' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="deploy_rootfs_rst-host-142" class="language-markup">sudo sfdisk /path/to/your/USB/device &lt;&lt; EOF
 0,
 EOF</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>


3. Format it as an *EXT2* partition:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'deploy_rootfs_rst-host-143' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="deploy_rootfs_rst-host-143" class="language-markup">sudo mkfs.ext2 /path/to/your/USB/device/partition</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

4. Extract your image inside such a media:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'deploy_rootfs_rst-host-144' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="deploy_rootfs_rst-host-144" class="language-markup">sudo tar -xjf /home/architech/architech_sdk/architech/hachiko-tiny/yocto/build/tmp/deploy/images/hachiko/tiny-image-hachiko.tar.bz2 -C /path/to/usb/media</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

5. Copy the kernel to the USB flash drive:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'deploy_rootfs_rst-host-145' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="deploy_rootfs_rst-host-145" class="language-markup">cp /home/architech/architech_sdk/architech/hachiko-tiny/yocto/build/tmp/deploy/images/hachiko/uImage /path/to/usb/media/boot</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

6. Now copy the device tree:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'deploy_rootfs_rst-host-146' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="deploy_rootfs_rst-host-146" class="language-markup">cp /home/architech/architech_sdk/architech/hachiko-tiny/yocto/build/tmp/deploy/images/hachiko/uImage-rza1-hachiko.dtb  /path/to/usb/media/boot/rza1-hachiko.dtb</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>


7. Unmount the flash drive from your system

8. Insert the USB Flash drive in the USB port at the bottom of the USB connector of Hachiko board