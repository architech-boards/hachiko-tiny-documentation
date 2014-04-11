Meta Layer
==========

A Yocto/OpenEmbedded meta-layer is a directory that contains recipes,
configuration files, patches, and others things all needed by Bitbake to
properly "see" and build a BSP, a distrubution, and a (set of) package(s).

meta-hachiko is stored in a git repository that can be cloned with:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'meta_layer_rst-host-181' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="meta_layer_rst-host-181" class="language-markup">git clone -b dora https://github.com/architech-boards/meta-hachiko.git</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

For information about Yocto, Bitbake and the directories tree inside the
meta-layer, please refer to the Yocto documentation.

Hachiko meta-layer defines two different machines: **hachiko** and **hachiko64**,
the latter to be used when an external SDRAM is available on the board.
Whereas *hachiko64* machine can be used for virtually any distro and image
available on Yocto, *hachiko* machine must use a custom tailored distro and image
to be able to fit in the limited amount of SRAM available on-chip.
This documentation is about hachiko.

To manually select board and distribution for *Bitbake*, make sure that file
*local.conf*, that in the SDK has this path:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'meta_layer_rst-host-182' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="meta_layer_rst-host-182" class="language-markup">/home/architech/architech_sdk/architech/hachiko-tiny/yocto/build/conf/local.conf</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

contains the assignment of these variables:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'meta_layer_rst-host-183' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="meta_layer_rst-host-183" class="language-markup">MACHINE = "hachiko"
 DISTRO = "tiny-linux-uclibc"</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

When asked to build an image, *Bitbake*/*Hob* produces several files as output, of
which these are needed to build the whole system:

* the Linux kernel - file *uImage*

* the device tree - file *uImage-rza1-hachiko.dtb*

* U-boot bootloader - file *u-boot.bin*

* the root file system - file *\*.tar.bz2* 

Within the SDK, the files will be emitted to directory:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'meta_layer_rst-host-184' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="meta_layer_rst-host-184" class="language-markup">/home/architech/architech_sdk/architech/hachiko-tiny/yocto/build/tmp/deploy/images/hachiko/</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

If you are not working with the SDK, just replace:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'meta_layer_rst-host-185' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="meta_layer_rst-host-185" class="language-markup">/home/architech/architech_sdk/architech/hachiko-tiny/yocto/build/</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

with your build directory path.