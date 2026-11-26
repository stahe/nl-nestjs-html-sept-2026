# Een webapplicatie maken met het framework NestJS

📖 **Lees de tutorial: [https://stahe.github.io/nl-nestjs-html-sept-2026/](https://stahe.github.io/nl-nestjs-html-sept-2026/)**

Deze cursus leert u hoe u met het framework [NestJS](https://nestjs.com) een **MVC**-webapplicatie bouwt: een applicatie waarvan de HTML-pagina's **door de server** worden gegenereerd met de view-engine Handlebars, zonder JavaScript-framework aan de clientzijde.

Hij volgt de opbouw van de cursus [Inleiding tot ASP.NET MVC aan de hand van voorbeelden](https://stahe.github.io/nl-aspnetmvc-nov-2013/) (2013), aangepast aan het Node.js/TypeScript-ecosysteem:

| ASP.NET MVC (2013) | NestJS (2026) |
|---|---|
| C#, controllers, acties | TypeScript, `@Controller`, `@Get`, `@Post` |
| Razor-views, `_Layout.cshtml` | Handlebars-views, `layout.hbs` |
| `[Required]`, `ModelState.IsValid` | class-validator, formuliervalidatie |
| sessie, `TempData` | cookies, JWT-token, flashberichten |
| filters, `[Authorize]` | middleware, guards, interceptors, `@Roles` |
| Entity Framework | TypeORM + MySQL |

## De aanpak: veel korte voorbeelden, daarna een casus

De cursus is gebaseerd op **28 korte projecten**, elk gericht op één enkel concept. U kunt ze uitvoeren en aanpassen. Alle voorbeelden delen één enkele `npm install`.

| Hoofdstuk | Inhoud | Voorbeelden |
|---|---|---|
| Controllers, acties, routing | routes, antwoorden, omleidingen, modules, dependency injection | 01–06 |
| Het actiemodel | parameters, conversie, validatie, POST-formulieren, pipes | 07–12 |
| De view en zijn template | Handlebars, templates, partials, helpers, formulieren, validatie, Post/Redirect/Get, bevestigingsvenster | 13–21 |
| Internationalisering | Een applicatie in het Frans en het Engels | 22 |
| Gegevensbereiken | Applicatie, aanvraag, client | 23 |
| De levenscyclus van een aanvraag | middleware, guard, interceptor, pipe, exception filter | 24 |
| Authenticatie en autorisatie | JWT in een cookie, rollen, CAPTCHA, rate limiting | 25 tot 27 |
| Gelaagde architectuur | web / bedrijfslogica / DAO met TypeORM, transacties, optimistische vergrendeling | 28 |

Elk voorbeeld wordt gepresenteerd met zijn volledige code en regel-voor-regelcommentaar. De cursus toont ook de resultaten tijdens de uitvoering: schermafbeeldingen van de browser, ruwe HTTP-antwoorden verkregen met `curl` en serverlogs.

## De casus: RdvMedecins

De casus is een complete applicatie voor het **plannen van afspraken bij een medische praktijk**. Hij bestaat uit ongeveer zestig bestanden, en **al** die bestanden worden opgesomd en toegelicht. Hij brengt alle concepten uit de voorgaande hoofdstukken samen.

- **Drie rollen:**
  - `ADMIN` beheert artsen en cliënten;
  - `DOCTOR` maakt afspraken en annuleert ze;
  - `USER` is de patiënt: hij maakt afspraken voor zichzelf en beheert zijn account.
- **Bedrijfsregels:**
  - geen afspraken in het verleden;
  - slechts één toekomstige afspraak per patiënt;
  - geen dubbele namen, dankzij benoemde uniciteitsbeperkingen;
  - een optimistische vergrendeling voorkomt dat een record wordt overschreven dat intussen door een andere gebruiker is gewijzigd.
- **Privacy:** een patiënt ziet nooit de namen van andere patiënten. Die naam wordt zelfs niet naar zijn browser gestuurd.
- **Beveiliging:**
  - JWT-token in een `httpOnly` / `sameSite`-cookie;
  - wachtwoorden gehasht met bcrypt;
  - CAPTCHA en tijdelijke blokkering na meerdere mislukte inlogpogingen;
  - het aanmaken van accounts beveiligd met een eenmalige „toegangscode".
- **Een tweetalige interface** (Frans/Engels), gebouwd met Bootstrap 5.
- **Progressive enhancement:** de applicatie werkt volledig zonder JavaScript. Een klein script voegt alleen een bevestigingsvenster toe dat met het toetsenbord kan worden bediend.

## Technologieën

NestJS 10 · TypeScript 5 · Express · Handlebars (hbs) · class-validator / class-transformer · TypeORM · MySQL 8 / MariaDB · Passport JWT · bcrypt · svg-captcha · Bootstrap 5

## Vereisten

- Basiskennis van TypeScript (of JavaScript), HTML en het HTTP-protocol.
- Node.js 20 of nieuwer, Visual Studio Code en een MySQL-server (bijv. Laragon onder Windows). Installatie-instructies staan in de bijlagen van de cursus.

## Auteur

Deze cursus, de voorbeelden en de casus zijn geschreven door **Claude**, de AI van [Anthropic](https://www.anthropic.com) (september 2026), in opdracht van **Serge Tahé**
