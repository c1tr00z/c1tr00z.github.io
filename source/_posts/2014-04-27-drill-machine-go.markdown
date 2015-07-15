---
layout: post
title: "Drill Machine Go!"
date: 2014-04-27 00:00:00 +0300
comments: true
categories: games gamedev compo ludum-dare
---

<!--more-->

<script type='text/javascript'>
	var gameName = "drill-machine-go";

	var unityObjectUrl = "http://webplayer.unity3d.com/download_webplayer-3.x/3.0/uo/UnityObject2.js";
		if (document.location.protocol == 'https:')
			unityObjectUrl = unityObjectUrl.replace("http://", "https://ssl-");
		document.write('<script type="text\/javascript" src="' + unityObjectUrl + '"><\/script>');

			var config = {
				width: 880, 
				height: 880,
				params: { enableDebugging:"0" }
				
			};
			var u = new UnityObject2(config);

			jQuery(function() {

				var $missingScreen = jQuery("#unityPlayer").find(".missing");
				var $brokenScreen = jQuery("#unityPlayer").find(".broken");
				$missingScreen.hide();
				$brokenScreen.hide();
				
				u.observeProgress(function (progress) {
					switch(progress.pluginStatus) {
						case "broken":
							$brokenScreen.find("a").click(function (e) {
								e.stopPropagation();
								e.preventDefault();
								u.installPlugin();
								return false;
							});
							$brokenScreen.show();
						break;
						case "missing":
							$missingScreen.find("a").click(function (e) {
								e.stopPropagation();
								e.preventDefault();
								u.installPlugin();
								return false;
							});
							$missingScreen.show();
						break;
						case "installed":
							$missingScreen.remove();
						break;
						case "first":
						break;
					}
				});
				u.initPlugin(jQuery("#unityPlayer")[0], "http://ctrz.me/unity/drill-machine-go/web.unity3d");
			});
</script>

<div id="unityPlayer">
	<div class="missing">
		<a href="http://unity3d.com/webplayer/" title="Unity Web Player. Install now!">
			<img alt="Unity Web Player. Install now!" src="http://webplayer.unity3d.com/installation/getunity.png" width="193" height="63" />
		</a>
	</div>
	<div class="broken">
		<a href="http://unity3d.com/webplayer/" title="Unity Web Player. Install now! Restart your browser after install.">
			<img alt="Unity Web Player. Install now! Restart your browser after install." src="http://webplayer.unity3d.com/installation/getunityrestart.png" width="193" height="63" />
		</a>
	</div>
</div>
<a href="http://yadi.sk/d/mCz6bKk9NRt9C"><img src="{{ root_url }}/images/builds/tux.png" title="Linux version" alt="Linux version"></a>

You are little drill machine and you want to see THE SURRRFACE! While you drill you move. Evil rockets want to kill you. Evade them and keed going to THE SURRRFACE!

For [Ludum Dare Compo 29](http://www.ludumdare.com/compo/ludum-dare-29/?action=preview&uid=36555)

Created with [Unity3D](http://unity3d.com)