# Freebox remote control

This project is a simple virtual remote control for Freebox V5 (HD).

It uses the deprecated HTTP API described here: https://dev.freebox.fr/bugs/task/4327

It consists in a single web page that should work on any browser, on desktop or mobile devices.

The API requires a secret code for the remote control that is stored in the browser local storage (localStorage) in an unsecured manner (plain text). This code is sent to freebox multimedia device as plain text also (Freebox V5 does not provide support for HTTPS).

Only the keys that I use on semi-regularly basis are implemented. There is no plan to implement other keys.

## Website

The project is deployed on Github Pages here: https://zeld.github.io/freebox-rc/freebox-rc.html

As Github pages requires HTTPS and the Freebox API is only available as HTTP only (for Freebox V5), the site is broken on Chrome based browsers (Mixed Content requests are completely blocked for security reasons since Chrome 81). As of current writing, it still works in Firefox (89) and Safari.


