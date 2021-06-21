# Freebox remote control

This project is a simple virtual remote control for freebox V5.

It uses the deprecated HTTP API described here: https://dev.freebox.fr/bugs/task/4327

It consists of a single web page that should work on any browser, on desktop or mobile devices. It is available here: https://zeld.github.io/freebox-rc/freebox-rc.html

Note: the site is actually broken on Chrome based browsers as Mixed Content request are now blocked for security reasons, and Freebox remote control API is not available as HTTPS.

The API requires a secret code for the remote control that is stored in the browser local storage (localStorage) in an unsecured manner (plain text) and sent to freebox multimedia device as plain text also (Freebox V5 does not seem to provide support for HTTPS).
