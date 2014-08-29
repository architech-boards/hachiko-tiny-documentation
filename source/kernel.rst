Linux Kernel
============

Build from sources
------------------

As seen for **U-Boot** in the previous section, the first step is to get the kernel
sources, which in this guide we assume that they will be copied to directory:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'kernel_rst-host-101' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="kernel_rst-host-101" class="language-markup">/home/architech/Documents/kernel</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

You are free to choose the path you like the most for the kernel sources, just remember
to replace the path used in this guide with your custom path.
The suggested way, even for the kernel, to get the sources is to take them from the Yocto
build directory (copying them in the aforementioned directory to avoid messing up Yocto):

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'kernel_rst-host-102' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="kernel_rst-host-102" class="language-markup">/home/architech/architech_sdk/architech/hachiko-tiny/yocto/build/tmp/work/hachiko-poky-linux-uclibceabi/linux/3.8.13-r2/linux-3.8.13/</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

or from the vanilla kernel tarball at this URL:

 `http://kernel.org/pub/linux/kernel/v3.0/linux-3.8.13.tar.bz2 <http://kernel.org/pub/linux/kernel/v3.0/linux-3.8.13.tar.bz2>`_.

and patch it using the patches found in Hachiko BSP meta-layer:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'kernel_rst-host-103' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="kernel_rst-host-103" class="language-markup">patch -p1 -d /home/architech/Documents/kernel &lt; /home/architech/architech_sdk/architech/hachiko-tiny/yocto/meta-hachiko/recipes-kernel/linux/files/0001-Imported-Renesas-patch-v2.0.0.patch
 patch -p1 -d /home/architech/Documents/kernel &lt; /home/architech/architech_sdk/architech/hachiko-tiny/yocto/meta-hachiko/recipes-kernel/linux/files/0002-Add-hachiko-support.patch</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>


If you are not developing from within the official SDK, the most general solution to check
them out and patch the sources is:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'kernel_rst-host-104' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="kernel_rst-host-104" class="language-markup">cd /home/architech/Documents
 git clone -b dora https://github.com/architech-boards/meta-hachiko.git
 patch -p1 -d /home/architech/Documents/kernel &lt; /home/architech/Documents/meta-hachiko/recipes-kernel/linux/files/0001-Imported-Renesas-patch-v2.0.0.patch
 patch -p1 -d /home/architech/Documents/kernel &lt; /home/architech/Documents/meta-hachiko/recipes-kernel/linux/files/0002-Add-hachiko-support.patch</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

To compile the kernel without bitbake just execute these commands:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'kernel_rst-host-105' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="kernel_rst-host-105" class="language-markup">cd /home/architech/Documents/kernel
 source /home/architech/architech_sdk/architech/hachiko-tiny/toolchain/environment-nofs
 make hachiko_defconfig
 make uImage dtbs</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

If you are not developing from within the original SDK, you are going to need to
:ref:`install the cross toolchain <manual_compilation_label>`.
The output of the compilation process is:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'kernel_rst-host-106' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="kernel_rst-host-106" class="language-markup">/home/architech/Documents/kernel/arch/arm/boot/uImage
 /home/architech/Documents/kernel/arch/arm/boot/dts/rza1-hachiko.dtb</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>
