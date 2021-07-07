# Freebox remote control

This project is a simple virtual remote control for Freebox V5 (HD).

It uses the deprecated HTTP API described here: https://dev.freebox.fr/bugs/task/4327

It consists in a single web page that should work on any browser, on desktop or mobile devices - provided the web page is hosted as HTTP or accessed locally (there are known issues with HTTPS hosting that are descibed below in the Security concerns section)

Only the keys that I use on semi-regularly basis are implemented. There is no plan to implement other keys.

## Security concerns
The API requires a security code for the remote control that is stored in the browser local storage (localStorage) in an unsecured manner (plain text). This security code is sent to freebox multimedia device as plain text also (Freebox V5 does not provide support for HTTPS).

If the web page is deployed as HTTPS there are known incompatibilities with Chrome based browsers as:
- The Freebox API is only available as HTTP (for Freebox V5) - and not HTTPS
- Chrome blocks all Mixed Content requests for security reasons - since version 81

A workaround is implemented to bypass this block on other browsers, but it's probably only a matter of time until those browsers completely block Mixed Content requests the same way Chrome does. As of current writing, the workaround still works in Firefox (89) and Safari.

## Website

The project is deployed on Github Pages here: https://zeld.github.io/freebox-rc/freebox-rc.html

As Github pages supports HTTPS only, the site is broken on Chrome based browsers for the reason explained above in the Security concerns section. 


