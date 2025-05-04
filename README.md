// login.js
const { default: makeWASocket, useSingleFileAuthState } = require("@adiwajshing/baileys");
const { Boom } = require("@hapi/boom");
const { state, saveState } = useSingleFileAuthState('./session.json');

async function startSock() {
    const sock = makeWASocket({
        auth: state,
        printQRInTerminal: true
    });
    sock.ev.on('creds.update', saveState);
}
startSock();
