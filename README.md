<!DOCTYPE html>
<html class="no-js" lang="en">
  <head>
  </head>
  <body>
    <div class="wrapAll clearfix">
      <div class="mainsection"><br>
        <div class="article">
          <h1><font style="font-size: 20pt" size="5"><span style="color:
                rgb(0, 0, 0); font-family: &quot;Times New Roman&quot;;
                font-size: 26.6667px; font-style: normal;
                font-variant-ligatures: normal; font-variant-caps:
                normal; font-weight: 400; letter-spacing: normal;
                orphans: 2; text-align: start; text-indent: 0px;
                text-transform: none; white-space: normal; widows: 2;
                word-spacing: 0px; -webkit-text-stroke-width: 0px;
                text-decoration-style: initial; text-decoration-color:
                initial; display: inline !important; float: none;">RS-Decoder
                for Radiosonde's in Ubuntu Linux</span>.</font> </h1>
          <p class="siteSub"><br>
          </p>
          <div class="articleRight"> <img src="img/rs1.png" alt="rs41s"
              width="82" height="280"><br>
            Vaisala RS-41<br>
          </div>
          <p style="user-select: auto !important; margin: 0px 0px 20px;
            padding: 0px; border: 0px; outline: 0px; font-size: 15px;
            vertical-align: baseline; background: 0px 0px rgb(255, 255,
            255); color: rgb(68, 68, 68); font-family: &quot;Helvetica
            Neue&quot;, sans-serif; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 300; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">A radiosonde is a
            small weather sensor package that is typically attached to a
            weather balloon. <br>
            As it rises into the atmosphere it measures parameters such
            as temperature, humidity, pressure, GPS location etc, and
            transmits this data back down to a receiver base station
            using a radio signal.<br>
            Zilog's<span>&nbsp;</span><a rel="noopener"
              href="https://github.com/rs1729/RS" target="_blank"
              style="user-select: auto !important; margin: 0px; padding:
              0px; font-size: 15px; vertical-align: baseline;
              background: 0px 0px; color: rgb(46, 110, 176);
              text-decoration: underline; -webkit-tap-highlight-color:
              rgb(0, 0, 0);">RS</a><span>-Decoders </span>is a free
            open source radiosonde decoder for Linux and it supports a
            wide range of radiosonde protocols. <br>
            Together with an RTL-SDR it is possible to receive
            radiosonde signals, and decode them using RS-Decoders.</p>
          <p style="user-select: auto !important; margin: 0px 0px 20px;
            padding: 0px; border: 0px; outline: 0px; font-size: 15px;
            vertical-align: baseline; background: 0px 0px rgb(255, 255,
            255); color: rgb(68, 68, 68); font-family: &quot;Helvetica
            Neue&quot;, sans-serif; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 300; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">This tutorial
            covers some tricky points like setting up audio piping in
            Linux CubicSDR or GQRX , and getting the GPS data into a
            virtual COM port to use with FoxtrotGPS.<br>
          </p>
          <br>
          <div class="contentsPanel">
            <div class="contentsHeader">Contents</div>
            <ul>
              <li> <span>1</span>Overview
                <ul>
                  <li><span>1.1&nbsp; <a href="#Dependencies_">Dependencies</a></span>
                  </li>
                  <li><span>1.2&nbsp; <a href="#Compile_Decoders_">Compile
                        Decoders</a></span> </li>
                  <li><span>1.3&nbsp; <a
                        href="#Scripts_Setting_up_Virtual_ports">Scripts,
                        Virtual Ports</a><br>
                    </span></li>
                  <li><span>1.4&nbsp; </span><a href="#SDR_Radio_programs_">SDR
                      Radio Programs</a></li>
                  <li>1.5&nbsp; <a href="#Install_Driver_">Install
                      Driver</a><br>
                  </li>
                  <li><span>1.6&nbsp; <a href="#Virtual_Audio_setup_">Virtual
                        Audio Setup</a></span> </li>
                  <li><span>1.7&nbsp; <a href="#GPSD_Setup_">GPSD Setup</a><br>
                    </span></li>
                  <li><span>1.8&nbsp; </span><a href="#Get_it_all_Running_">Get
                      it all running</a><a
                      href="#Zilog_DFM_Decoder_Scripts_"><br>
                    </a></li>
                </ul>
              </li>
            </ul>
          </div>
          <br>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"> </p>
          <h2><a name="Dependencies_"></a>Dependencies<br>
          </h2>
          <div class="articleRight">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img
              src="img/imet.png" alt="imet" width="133" height="174">&nbsp;
            <br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Intermet I-Met 1AB
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            <br>
          </div>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">Make sure you have
            sox, perl, gpsd, socat and pulseaudio installed.</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">sudo apt-get
            install sox</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">sudo apt-get
            install perl</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">sudo apt-get
            install socat</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">sudo apt-get
            install pulseaudio</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">sudo apt-get
            install pavucontrol</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">sudo apt-get
            install gpsd gpsd-clients</p>
          <h2><a name="Compile_Decoders_"></a>Compile Decoders<br>
          </h2>
          <div class="articleRight">&nbsp;&nbsp;&nbsp; &nbsp; &nbsp;
            &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; <img src="img/rs1.png"
              alt="rs41" width="82" height="280">&nbsp; <br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            Vaisala RS-41&nbsp; SGP
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            <br>
          </div>
          <br>
          <a href="img/files.zip"><b>Download Decoders and Script</b></a><br>
          <br>
          <a href="http://happysat.nl/RS/Ubuntu/" target="_blank">Updated
            compiled RS-Decoders are overhere.</a><br>
          <br>
          <p> <a href="#Scripts_Setting_up_Virtual_ports">And skip this
              part.</a><br>
            <br>
          </p>
          <b>Or create manually</b><br style="color: rgb(0, 0, 0);
            font-family: &quot;Times New Roman&quot;; font-size: medium;
            font-style: normal; font-variant-ligatures: normal;
            font-variant-caps: normal; font-weight: 400; letter-spacing:
            normal; orphans: 2; text-align: start; text-indent: 0px;
            text-transform: none; white-space: normal; widows: 2;
            word-spacing: 0px; -webkit-text-stroke-width: 0px;
            text-decoration-style: initial; text-decoration-color:
            initial;">
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">Download the
            decoders or just do a git clone</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">wget<span>&nbsp;</span><a
              href="https://github.com/rs1729/RS/archive/master.zip"
              target="_blank">https://github.com/rs1729/RS/archive/master.zip</a></p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">git clone
            git://github.com/rs1729/RS.git<br>
          </p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">Compile decoders
            DFM-09/RS-41/M10, M20 or any other you need.</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">cd RS/demod/mod<br>
            gcc -c demod_mod.c -w -O3<br>
            gcc -c bch_ecc_mod.c -w -O3</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">echo "Compiling
            Mod RS41" <br>
            gcc rs41mod.c demod_mod.o bch_ecc_mod.o -lm -O3 -o rs41mod
            -w<br>
            <br>
            echo "Compiling Mod DFM09" <br>
            gcc dfm09mod.c demod_mod.o -lm -O3 -o dfm09mod -w<br>
            <br>
            echo "Compiling Mod M10/20" <br>
            gcc m10mod.c demod_mod.o -lm -O3 -o m10mod -w<br>
            gcc mXXmod.c demod_mod.o -lm -O3 -o mXXmod -w<br>
            <br>
          </p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">Put compiled
            rs41mod and dfm09mod files in a folder decoders or smth.<br>
            <b>Also put pos2nmea.pl (NMEA perl script) from folder
              RS/tools in the folder!</b><br>
          </p>
          <h2><a name="Scripts_Setting_up_Virtual_ports"></a>Scripts,
            Setting up Virtual ports<br>
          </h2>
          <div class="articleRight">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img
              src="img/rs92.png" alt="rs92" width="179" height="329">&nbsp;
            <br>
            &nbsp;&nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
            Vaisala RS-92
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            <br>
          </div>
          We need to create a few scripts..
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Example DFM:</b></p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">Create new file
            dfm.sh with content:</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">#!/bin/bash<br>
            echo "DFM Log" &gt; /home/decoders/dfm09_`date
            +%Y%m%d%H`Z.txt<br>
            sox -t pulseaudio default -t wav - 2&gt;/dev/null |
            ./dfm09mod --dist -vv --ptu --auto 2&gt;&amp;1 | tee -a
            /home/decoders/dfm09_`date +%Y%m%d%H`Z.txt | ./pos2nmea.pl
            &gt; /tmp/virtualcom0<br>
            exit </p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Save it</b>.<br>
            <br>
          </p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Making Virtual
              COM Port.</b></p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">Create new file
            vp.sh with content:</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">#!/bin/bash<br>
            <br>
            echo "Creating Virtual Com Port: 0 and 1"<br>
            <br>
            vcpath='/tmp'<br>
            socat -d -d pty,link=${vcpath}/virtualcom0,raw,echo=0
            pty,link=${vcpath}/virtualcom1,raw,b4800,echo=0 &amp;<br>
            socatpid=$!<br>
            echo "socat pid=$socatpid"<br>
            sleep 2<br>
            <br>
            trap "kill $socatpid &amp;&gt;/dev/null; exit 0" INT TERM
            EXIT<br>
            <br>
            echo "Start GPSD on Virtual Com Ports"<br>
            killall -q gpsd<br>
            gpsd -D2 -b -n -N ${vcpath}/virtualcom1</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Save it.</b></p>
          <img src="img/vp1.jpg" alt="vp1" width="486" height="343"><br>
          <br>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Create new file
              dfm_gps.sh with content:</b></p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">#!/bin/sh</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">xfce4-terminal -T
            vp -e ./vp.sh --tab -T dfm -e ./dfm.sh</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Save i</b><b>t.</b></p>
          <br style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Create new file
              rs41.sh with content:</b></p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">#!/bin/bash<br>
            sleep 1<br>
            sox -t pulseaudio default -t wav - 2&gt;/dev/null |
            ./rs41mod --ecc2 --crc -vx --ptu 2&gt;&amp;1 | tee -a
            /home/decoders/rs41_`date +%Y%m%d%H`Z.txt&nbsp; |
            ./pos2nmea.pl &gt; /tmp/virtualcom0<br>
            exit</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Save it.</b></p>
          <br style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Create new file
              rs41_gps.sh with content:</b></p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">#!/bin/sh<br>
            xfce4-terminal -T vp -e ./vp.sh&nbsp; --tab -T rs41 -e
            ./rs41.sh </p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Save it.</b></p>
          <span style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"> </span>
          <div class="articleRight">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            <img src="img/dfm06.png" alt="dfm06" width="52" height="65">&nbsp;
            <br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Graw DFM-06
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </div>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><br>
          </p>
          <span style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>chmod 755 all
              created scripts :)<br>
              <br>
            </b>
            <p><b>Add username to dailout Group for COM port
                access/permissions:</b><br>
            </p>
            <p>sudo adduser &lt;your_username&gt; dialout<br>
              <br>
            </p>
            <p><b>Make permissions for COM ports:</b></p>
            <p>sudo chown -R &lt;your_username:your_username&gt;
              /tmp/virtualcom0</p>
          </span><span style="color: rgb(0, 0, 0); font-family:
            &quot;Times New Roman&quot;; font-size: medium; font-style:
            normal; font-variant-ligatures: normal; font-variant-caps:
            normal; font-weight: 400; letter-spacing: normal; orphans:
            2; text-align: start; text-indent: 0px; text-transform:
            none; white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">
            <p>sudo chown -R &lt;your_username:your_username&gt;
              /tmp/virtualcom1</p>
          </span><span style="color: rgb(0, 0, 0); font-family:
            &quot;Times New Roman&quot;; font-size: medium; font-style:
            normal; font-variant-ligatures: normal; font-variant-caps:
            normal; font-weight: 400; letter-spacing: normal; orphans:
            2; text-align: start; text-indent: 0px; text-transform:
            none; white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"></span><span
            style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"></span><span
            style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"></span><span
            style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"></span><span
            style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"></span><span
            style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"></span><span
            style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">
            <p>When you got errors, run ./vp.sh so the virtual ports are
              accessible in /tmp for setting chown permissions.</p>
            <p><br>
              <b>Note:</b><br>
            </p>
            <p>This tutorial was written using Ubuntu 16.04, on newer
              distro's you might have to change: <br>
            </p>
            <p>sox -t pulseaudio default into sox -t alsa default<br>
              If a wav error happens.<br>
              <br>
            </p>
            <p><b>What does it all mean:</b></p>
            <p><b>rs41mod -h</b><br>
              rs41mod [options] audio.wav<br>
              &nbsp; options:<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -v, -vx, -vv&nbsp;
              (info, aux, info/conf)<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -r, --raw<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -i, --invert<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; --ths
              &lt;x&gt;&nbsp;&nbsp;&nbsp; (peak threshold; default=0.7)<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
              --iq0,2,3&nbsp;&nbsp;&nbsp; (IQ data)<br>
              <br>
            </p>
            <p><b>dfm09mod -h</b><br>
              dfm09mod [options] audio.wav<br>
              &nbsp; options:<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -v, -vv<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -r, --raw<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -i, --invert<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
              --ecc&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (Hamming
              ECC)<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; --ths
              &lt;x&gt;&nbsp;&nbsp;&nbsp; (peak threshold; default=0.6)<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
              --json&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (JSON output)<br>
              <br>
            </p>
            <p>--ecc2 now also gives the output after each block how
              many bits the error correction has corrected.&nbsp; <br>
              --ptu temperature Info<br>
              --dist is like ecc, but only blocks that belong to the
              same frame are taken, i. if errors occur, the frame is
              discarded / Inversed used for DFM06/09.<br>
              <span style="color: rgb(0, 0, 0); font-family: &quot;Times
                New Roman&quot;; font-size: medium; font-style: normal;
                font-variant-ligatures: normal; font-variant-caps:
                normal; font-weight: 400; letter-spacing: normal;
                orphans: 2; text-align: start; text-indent: 0px;
                text-transform: none; white-space: normal; widows: 2;
                word-spacing: 0px; -webkit-text-stroke-width: 0px;
                text-decoration-style: initial; text-decoration-color:
                initial;"></span></p>
          </span>
          <h2><a name="Install_Driver_"></a>Install
            Driver&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            <br>
          </h2>
          <br>
          <b>Install RTL-SDR-Blog Driver (or any other):</b><br>
          <br>
          git clone git://github.com/rtlsdrblog/rtl-sdr-blog.git<br>
          cd rtl-sdr-blog/<br>
          mkdir build<br>
          cd build<br>
          cmake ../ -DINSTALL_UDEV_RULES=ON -DDETACH_KERNEL_DRIVER=ON<br>
          make<br>
          sudo make install<br>
          sudo ldconfig<br>
          sudo cp ../rtl-sdr.rules /etc/udev/rules.d/<br>
          echo blacklist dvb_usb_rtl28xxu &gt;&gt; blacklist-rtl.conf<br>
          echo blacklist rtl2832 &gt;&gt; blacklist-rtl.conf<br>
          echo blacklist rtl2830 &gt;&gt; blacklist-rtl.conf<br>
          sudo cp blacklist-rtl.conf /etc/modprobe.d/<br>
          <br>
          For list of improvements visit: <a
            href="https://github.com/rtlsdrblog/rtl-sdr-blog"
            target="_blank">https://github.com/rtlsdrblog/rtl-sdr-blog</a><span
            style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"> </span>
          <h2><a name="SDR_Radio_programs_"></a>SDR Radio programs<br>
          </h2>
          <div class="articleRight">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img
              src="img/Imet4.png" alt="imet4" width="132" height="235">&nbsp;
            <br>
            &nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp;&nbsp; Intermet I-Met
            4
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            <br>
          </div>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><br>
            <b>Install Gqrx, 3 options:</b></p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">sudo apt-get
            install gqrx<br>
            <b>You get an old Gqrx version in Ubuntu 16.04 and no
              updates.</b><br>
          </p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"> <br>
          </p>
          <img src="img/Gqrx.png" alt="" width="568" height="374"><br>
          <br>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">Follow<span>&nbsp;</span><a
              href="http://gqrx.dk/download/install-ubuntu"
              target="_blank">Install Gqrx SDR on Ubuntu Linux</a><span>&nbsp;</span>and
            add PPA for install.</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">Or fast way
            (without GNU Radio setup) Download<span>&nbsp;</span><a
              href="https://github.com/csete/gqrx/releases"
              target="_blank">Gqrx Appimage</a>:<br>
            chmod a+x Gqrx-2.11.5-x86_64.AppImage<br>
            And run,</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">./Gqrx-2.11.5-x86_64.AppImage</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><br>
          </p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">CubicSDR, build
            from source or use<span>&nbsp;</span><a
              href="https://github.com/cjcliffe/CubicSDR/releases/"
              target="_blank">Appimage</a><br>
            chmod a+x CubicSDR-0.2.5-x86_64.AppImage<br>
            And run,</p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">./CubicSDR-0.2.5-x86_64.AppImage</p>
          <img src="img/Cubic.jpg" alt="cubic" width="584" height="397"><br>
          <br>
          <h2><a name="Virtual_Audio_setup_"></a>Virtual Audio setup<br>
          </h2>
          <div class="articleRight">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img
              src="img/dfm09.png" alt="dfm09" width="226" height="167">&nbsp;
            <br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            <br>
            &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
            &nbsp; &nbsp; &nbsp;&nbsp;&nbsp; Graw DFM-09
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            <br>
          </div>
          <br>
          <b>Some virtual audio can be setup: </b>
          <p>Adding these lines to this file ~/.config/pulse/default.pa
            on Ubuntu 16.04, newer distro's have to change
            /etc/pulse/default.pa:</p>
          <p>load-module module-null-sink sink_name=VBCable_A
            sink_properties=device.description="VBCable_A"<br>
            load-module module-null-sink sink_name=VBCable_B
            sink_properties=device.description="VBCable_B" </p>
          <p><br>
          </p>
          <p>Will always load the desired NULL sinks on starting the
            pulseaudio sound server.<br>
            Removing sinks that had been loaded by pactl or pacmd, i.e.
            without settings in our default.pa can most quickly done by<b>
              pulseaudio -k</b><br>
          </p>
          <p>This command will kill the running pulseaudio instance, to
            instantaneaously respawn it (in a default set up) using
            values defined in the default.pa. <br>
            Start SDR App tune in on WX-Station that launches DFM/RS or
            any Radiosonde you prefer.</p>
          <p><br>
            It is recommend disabling PulseAudio logging, as this seems
            to be a large user of CPU cycles.<br>
            <br>
            Edit /etc/pulse/daemon.conf<br>
            Now find "log-level" and change it to "log-level = error". <br>
            Remove the semi-colon on the log-level line too. Save and
            exit.<br>
            <br>
            ; log-target = auto<br>
            log-level = error<br>
            ; log-meta = no<br>
            You can now reload pulseaudio either by rebooting, or
            running "pulseaudio -k" at a command line.<br>
            <br>
          </p>
          <img src="img/va.jpg" alt="audio" width="451" height="324"><br>
          <br>
          <img src="img/va2.jpg" alt="audio2" width="451" height="324"><br>
          <br>
          <p><b>Dont forget PVAControl to setup the Virtual audio!</b></p>
          <h2><a name="GPSD_Setup_"></a>GPSD Setup<br>
          </h2>
          <div class="articleRight">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img
              src="img/Ozon.png" alt="o3" width="194" height="185">&nbsp;
            <br>
            &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Vaisala
            RS-92 Ozon
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            <br>
          </div>
          <br>
          In order to use gpsd with the decoder, we have to disable the
          service.
          <p>So it can be manually started:</p>
          <p>sudo systemctl stop gpsd.socket<br>
            sudo systemctl disable gpsd.socket </p>
          <p>Should you ever want to enable the default gpsd systemd
            service you can run these commands to restore it:</p>
          <p>sudo systemctl enable gpsd.socket<br>
            sudo systemctl start gpsd.socket <br>
            <br>
          </p>
          <p>Start script ./dfm_gps.sh or ./rs41_gps.sh</p>
          <p>It will execute the script in 4 tabs terminals(vp and the
            chosen decoder).<br>
            The sleep commands are inserted so other processes(
            socat/gpsd) do not start before the decoder.<br>
          </p>
          <br>
          <p>It will create with socat 2 pairs of Virtual Com Ports, 1
            out other in, execute binary file.<br>
            NMEA data will be shown and the decoder.<br>
          </p>
          <p style="margin-bottom: 0in">As long as the socat (Terminal
            vp) is running, you have a pair of VPs open.</p>
          They are named virtualcom 0 and 1 so they stay static and no
          dev/pts/ number change.
          <p> </p>
          <h2><a name="Get_it_all_Running_"></a>Get it all Running<br>
          </h2>
          <p>Need some GPS Applications to show Radiosonde position:</p>
          <p><b>sudo apt-get instal foxtrotgps</b><br>
          </p>
          <p>Will install older FoxtrotGPS version from feed.<br>
          </p>
          <p> <img src="img/map_osm.png" alt="" width="556"
              height="401"><br>
            <br>
          </p>
          <p><b>For newer versions build from source:</b><br>
            Dependencies - <a
              href="https://www.foxtrotgps.org/build.html"
              target="_blank">https://www.foxtrotgps.org/build.html</a><br>
            Download <a href="https://www.foxtrotgps.org/releases/"
              target="_blank">source</a> on FoxtrotGPS website.<br>
          </p>
          <p> &nbsp;</p>
          <p> <b>Insert extra Maps for FoxtrotGPS.</b><br>
            Open FoxtrotGPS, goto Info Icon 3th screen, Map type's New:<br>
            <br>
          </p>
          <p><img src="img/FoxtrotGPS_Map.png" alt="" width="553"
              height="399"><br>
            <br>
          </p>
          <p> http://tile.memomaps.de/tilegen/%d/%d/%d.png<br>
            <br>
          </p>
          <p> <img src="img/map_dark.png" alt="" width="586"
              height="423"></p>
          <p><br>
            For Thunderforest maps sign up free at their <a
              href="https://www.thunderforest.com/" target="_blank">website</a>
            to get api-key and insert it into the links below:<br>
            <br>
          </p>
          <p> <b>Example</b>:<br>
          </p>
          <p>thunderforest_api_key = 123</p>
          https://tile.thunderforest.com/pioneer/%d/%d/%d.png?apikey=123<br>
          https://tile.thunderforest.com/cycle/%d/%d/%d.png?apikey=123<br>
https://tile.thunderforest.com/transport/%d/%d/%d.png?apikey=123<br>
https://tile.thunderforest.com/landscape/%d/%d/%d.png?apikey=123<br>
https://tile.thunderforest.com/outdoors/%d/%d/%d.png?apikey=123<br>
https://tile.thunderforest.com/transport-dark/%d/%d/%d.png?apikey=123<br>
https://tile.thunderforest.com/spinal-map/%d/%d/%d.png?apikey=123<br>
https://tile.thunderforest.com/neighbourhood/%d/%d/%d.png?apikey=123<br>
https://tile.thunderforest.com/mobile-atlas/%d/%d/%d.png?apikey=12<br>
          <br>
          <p><b>Install Navit.</b><br>
            sudo apt-get install navit<br>
            <br>
          </p>
          <p>It's recommended to follow this excellent guide about
            navit:<br>
          </p>
          <p><a
              href="http://ozzmaker.com/navigating-navit-raspberry-pi/"
              target="_blank">http://ozzmaker.com/navigating-navit-raspberry-pi/</a></p>
          <p>Download Offline Navit OSM Map's:<br>
          </p>
          <p> <a href="http://maps3.navit-project.org/">http://maps3.navit-project.org/</a>
          </p>
          <br>
          Tune in on a Radiosonde, run scripts.<br>
          <br>
          <img src="img/dfm_mod.png" alt="" width="347" height="237"><br>
          <p>Start FoxtrotGPS or Viking GPS to show Radiosonde current
            location and track.<br>
            <br>
          </p>
          <img src="img/Viking.jpg" alt="vik" width="615" height="403"><br>
          <br>
          <p>Foxtrot gpsd-port: 2947</p>
          <br>
          <img src="img/Foxtrot.jpg" alt="fox" width="614" height="444"><br>
          <br>
          <br>
          <img src="img/all.jpg" alt="" width="1139" height="716"><br>
          <br>
        </div>
        <div class="pagefooter">
          <p>Thanks fly out to Zilog80, Andreas6 and Flux242 for
            simplifying Virtual-ports.<br>
          </p>
  </body>
</html>
