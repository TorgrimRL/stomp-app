
# STOMP‑app

Et enkelt Spring Boot‑prosjekt som demonstrerer STOMP‑over‑WebSocket.

##  Komme i gang

### Forutsetninger
- Java 17
- Gradle (Wrapper inkludert)
- Git

### Bygg og kjør

# Klon og gå til mappen
```
git clone git@github.com:TorgrimRL/stomp-app.git
cd stomp-app
```
# Bygg prosjektet
```
./gradlew clean build
```
# Start serveren
```
./gradlew bootRun
```

Serveren vil lytte på `http://localhost:8080` og WebSocket‑endepunktet `/mywebsocket`.

## ⚙️ Hvordan det fungerer

1. **WebSocketConfig**
   Konfigurerer STOMP‑endepunkt (`/mywebsocket`) og:

   * Broker‑prefix `/topic`
   * Applikasjons‑prefix `/app`

2. **GreetingController**

   * `@MessageMapping("/hello")` mottar meldinger sendt til `/app/hello`
   * `@SendTo("/topic/greetings")` sender svar til alle abonnenter på `/topic/greetings`

3. **Klient (StompClient)**

   * Koble til via `ws://localhost:8080/mywebsocket`
   * Abonner på `/topic/greetings`
   * Send melding til `/app/hello`

Hver instans abonnerer på `greetings` og mottar alle meldinger.


