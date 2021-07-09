# Freebox remote control

This project is a minimalistic virtual remote control for Freebox V5 (HD).

It uses the deprecated [Freebox remote control HTTP API](https://dev.freebox.fr/bugs/task/4327) to send simple HTTP requests to the Freebox HD device: `GET http://hd1.freebox.fr/pub/remote_control?code=<security_code>&key=<remote_control_key>`

The projects consists in a single Web page that should work on any browser, on desktop or mobile devices - although there are known issues with HTTPS hosting that are descibed below, due to the limitations of the Freebox V5 API.

Requirements are:
- To open the Web page in a browser that is connected to the local Freebox network (using wifi or ethernet)
- To configure the virtual remote security code (available in the parameters of Freebox TV)

Project goals:
- Provide a virtual remote control as a minimalist and self-contained Web page
- Displays OK on phones

Non goals:
- Support any kind of device such PC, tablet
- Support any types of Freebox
- Fancy UI

Only the keys that I use on semi-regularly basis are implemented. There is no plan to implement other keys.

## Website

The project is deployed on Github Pages here: https://zeld.github.io/freebox-rc/freebox-rc.html

As Github pages supports HTTPS only, the site is broken on Chrome based browsers for reasons explained in the Security section.

## Compatibility

Due to security reasons explained below there are some known restrictions when using the project on Chrome based browsers, depending on the protocol that is used to open the Web page.

| Protocol        | Chrome           | Firefox  | Edge (Chrome based) | Safari
| --------------- | ---------------- | -------- | ------------------- | ------
| file://         | OK               | OK       | Not tested          | Not tested
| http://         | OK               | OK       | Not tested          | OK
| https://        | Broken since 81  | OK       | Presumably broken   | OK

## Security

The Freebox remote control API requires a security code. Since this security code is transferred in an inherently insecure manner (as plain text as part of an HTTP request) to the Freebox HD (as the API is available as HTTP only on Freebox V5 and HTTPS is not supported) there is no attempt to provide any security in this project. As such the security code is simply stored in the browser local storage (localStorage) in an unsecured manner (plain text).

When the Web page is deployed as HTTPS (such as Github pages) there are known incompatibilities with Chrome based browsers as:
- The Freebox API is only available as HTTP (for Freebox V5) - and not HTTPS
- Chrome blocks all Mixed Content requests for security reasons - since version 81

A workaround is implemented to bypass this block on other browsers, but it's probably only a matter of time until those browsers completely block Mixed Content requests the same way Chrome does. As of current writing, the workaround still works in Firefox (89) and Safari.


