import { useState, useEffect, useRef } from "react";

// ─── STAFF & AUTH ────────────────────────────────────────────────────
const STAFF = [
  { id:"admin", name:"Thinesh", pin:"1234", role:"admin", avatar:"TK" },
  { id:"12", name:"Jatharthan Muthulingam", pin:"1001", role:"ansatt", avatar:"JM" },
  { id:"1001", name:"Yousef Ahmad", pin:"1002", role:"ansatt", avatar:"YA" },
  { id:"20117", name:"Christine Joy Daria", pin:"1003", role:"ansatt", avatar:"CJ" },
  { id:"501256", name:"Shahad Dawood Al-Obaidi", pin:"1004", role:"ansatt", avatar:"SA" },
  { id:"501804", name:"Nathan Mpoyi", pin:"1005", role:"ansatt", avatar:"NM" },
  { id:"502269", name:"Zabiullah Sanwari", pin:"1006", role:"ansatt", avatar:"ZS" },
  { id:"503213", name:"Mansoor Redi", pin:"1007", role:"ansatt", avatar:"MR" },
  { id:"507884", name:"Emil Hennaen Linder", pin:"1008", role:"ansatt", avatar:"EL" },
];

const LOGO = "data:image/png;base64,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";

// ─── DATA ────────────────────────────────────────────────────────────
const CHECKLISTS = {
  apning: {
    title: "Åpningsvakt Helg", icon: "☀️",
    sections: [
      { title: "Ved ankomst (kl. 07:00)", tasks: [
        { id: 1, task: "Sjekk ute-bukk og lys ute" }, { id: 2, task: "Telle kassen (2 000 kr) og stemple inn på tidsbanken" },
        { id: 3, task: "Slå på musikk" }, { id: 4, task: "Ta ut boller og sett dem på heving", note: "Bruk liste" },
        { id: 5, task: "Steke pølser: 6 bacon, 2 hamburger, 3 grill, 2 wiener" },
        { id: 6, task: "Sjekke filterkaffe" }, { id: 7, task: "Klargjøre kaffemaskinene 100 %" },
      ]},
      { title: "Morgenoppgaver", tasks: [
        { id: 8, task: "Steke opp bakevarer" }, { id: 9, task: "Lage baguetter" }, { id: 10, task: "Pakke 3-pk boller" },
        { id: 11, task: "Steke opp 4 pizzaslice", note: "Husk sjekke vann" },
        { id: 12, task: "Fylle på pølser og garnityr – ta temperatur", note: "Lage liste" },
        { id: 13, task: "Etterfylle matdisken" }, { id: 14, task: "Etterfylle bakeriskap og kaker" },
        { id: 15, task: "Pakke Too Good To Go og legge ut", note: "Verdi 118 kr i utpris" },
      ]},
      { title: "Renhold og vedlikehold", tasks: [
        { id: 16, task: "Skrive røyk- og snusliste", note: "Bruk liste" }, { id: 17, task: "Vaske kassediskene grundig" },
        { id: 18, task: "Vaske filter på highspeed" }, { id: 19, task: "Vaske stekeskål i highspeed" },
        { id: 20, task: "Telle svinnbøtten" }, { id: 21, task: "Vaske sirupflaskene" },
        { id: 22, task: "Fylle på dressing foran pølsedisken" },
        { id: 23, task: "Vaske glass: pølsedisk, matdisk, kjøl (foran og bak)" },
        { id: 24, task: "Kutte opp råløk" }, { id: 25, task: "Tømme oppvaskmaskin" },
        { id: 26, task: "Støvsuge bak kassen" }, { id: 27, task: "Vaske grundig bak kassen" },
        { id: 28, task: "Vaske og rydde inni skapene bak kassen" }, { id: 29, task: "Rengjøre vaskene med skurekrem" },
        { id: 30, task: "Vaske bestikk og sortere dem" }, { id: 31, task: "Vaske alle brett som er tatt i bruk" },
        { id: 32, task: "Vaske pizzaskap + steke opp pizza 2–4 slice" },
        { id: 33, task: "Kontrollere fryskjølen bak kasse" }, { id: 34, task: "Hente opp servietter, bolleposer osv.", note: "SE BAK" },
        { id: 35, task: "Sjekke bananer og epler" }, { id: 36, task: "Fronte og face varer ute i butikk" },
        { id: 37, task: "Sjekke dato på yoghurt, smoothie, sandwich og wraps" },
        { id: 38, task: "Fylle på paraplyer dersom det trengs" }, { id: 39, task: "Tømme boss og vaske gulvet" },
      ]},
      { title: "Påfyll (fra kl. 10:00)", tasks: [
        { id: 40, task: "Rulle bacon" }, { id: 41, task: "Lage tacobaguetter" }, { id: 42, task: "Lage surdeigsandwich" },
        { id: 43, task: "Sette opp pizza inne på kjølen" }, { id: 44, task: "Fylle på hovedkjøl" },
        { id: 45, task: "Rydde hovedkjøl og ta ut boss" }, { id: 46, task: "Fylle på kjølene ute" },
        { id: 47, task: "Fylle på chipshyllen" }, { id: 48, task: "Fylle på kioskvarer" }, { id: 49, task: "Fylle på posegodt" },
      ]},
      { title: "Fra kl. 16:00 – Avslutning", tasks: [
        { id: 50, task: "Fjerne traktekaffe og rengjøre kolbene" },
        { id: 51, task: "Trekke fram, fronte og face varer og drikker", note: "Når du har tid" },
        { id: 52, task: "Vaske glass" }, { id: 53, task: "Skifte vann i oppvaskmaskin og wienerkoker" },
        { id: 54, task: "Rydde bak kassen, vaske kassedisk, rengjøre vasker, tømme alt", note: "Siste gjennomgang" },
      ]},
    ],
  },
  start: {
    title: "Startliste", icon: "🟢",
    sections: [
      { title: "Ved oppstart", tasks: [
        { id: 1, task: "Ren og riktig uniform" },
        { id: 2, task: "Personlig hygiene (hår i strikk, korte negler, ingen neglelakk)" },
        { id: 3, task: "Telle kassen – begynn med 2 000 kr", note: "Husk dagsrapport" }, { id: 4, task: "Vaske hender" },
      ]},
      { title: "Kaffemaskin", tasks: [
        { id: 5, task: "Vaske på og rundt maskinen med klut og D10" }, { id: 6, task: "Fylle på kaffebønner og melk" },
        { id: 7, task: "Fylle på sukker og rørepinner" }, { id: 8, task: "Vaske sirupflaskene + hyllen" },
      ]},
      { title: "Dressingbord", tasks: [
        { id: 9, task: "Vask dressingflaskene og bordet, tørk tuppene" }, { id: 10, task: "Slå sammen like dresssinger" },
        { id: 11, task: "Hent nye fra kjølen om det er lite" },
      ]},
      { title: "Ismaskin", tasks: [
        { id: 12, task: "Rør om i isen, fjern is rundt kantene" }, { id: 13, task: "Vask pinnen og lokket i varmt vann" },
        { id: 14, task: "Plasser pinnen og lokket tilbake" }, { id: 15, task: "Sjekk at maskinen står på iskrem" },
      ]},
      { title: "Pølsedisk", tasks: [
        { id: 16, task: "Sjekk pølsebrød (2 fine, 2 grove)" }, { id: 17, task: "Sjekk nok pølser i skuffen" },
        { id: 18, task: "Sjekk vann i wienerkoker" }, { id: 19, task: "Vask garnityrskuffen, bytt skåler/skjeer" },
        { id: 20, task: "Sjekk om det trengs mer baconpølse" },
      ]},
      { title: "Pizzaskap", tasks: [
        { id: 21, task: "Sjekk vann i skuffen" }, { id: 22, task: "Sjekk om det trengs ny pizza" },
        { id: 23, task: "Svinn gammel pizza" },
      ]},
      { title: "Butikkstandard – kontinuerlig", tasks: [
        { id: 24, task: "Sjekk butikken, vask om nødvendig" }, { id: 25, task: "Trekk frem og face alle varer" },
        { id: 26, task: "Sjekk matdisken, skift brett" }, { id: 27, task: "Sjekk dato på varer" },
        { id: 28, task: "Svinn utgåtte varer → TooGoodToGo" }, { id: 29, task: "Sjekk frukten" },
        { id: 30, task: "Vask glass med JIF universal" }, { id: 31, task: "Vask metall med Taski" },
        { id: 32, task: "Vaske klyper, bestikk, utstyr" }, { id: 33, task: "Tømme/vaske oppvaskmaskin + filter" },
        { id: 34, task: "Vaske/rydde kjølen, tørke hyller" }, { id: 35, task: "Fylle på drikke" },
        { id: 36, task: "Sjekk gulvet" }, { id: 37, task: "Vask vaskene med skurekrem" },
      ]},
    ],
  },
  slutt: {
    title: "Sluttliste", icon: "🔴",
    sections: [
      { title: "Før vaktens slutt", tasks: [
        { id: 1, task: "Butikkstandard: topp stand til nestemann", note: "Trekk frem, face, tørk, rydd" },
        { id: 2, task: "Tømme boss – gå ut med restavfall og papp", note: "Brett papp!" },
        { id: 3, task: "Sørg for rent rundt vasken" }, { id: 4, task: "Tømme og rengjøre oppvaskmaskin" },
        { id: 5, task: "Sjekke vann i pizzaskap og wienerkoker" }, { id: 6, task: "Vaske over gulvet" },
        { id: 7, task: "Hente opp ting som mangler", note: "Sjekk kluter og mopper!" },
        { id: 8, task: "Ta ned skitne kluter og mopper" },
        { id: 9, task: "Ta med ned tomme flasker/bokser", note: "Pantesekk nede" },
      ]},
      { title: "Kasseoppgjør", tasks: [
        { id: 10, task: "Telle kassen – 2 000 kr skal ligge igjen" },
        { id: 11, task: "Kontanter i oppgjørspose → safen" },
        { id: 12, task: "Gå opp og droppe", note: "Dropp på ditt navn!" },
      ]},
    ],
  },
};

const SHIFTS_TEMPLATE = [
  { day: "Mandag", slots: [{ time: "07–15", name: "" }, { time: "15–23", name: "" }] },
  { day: "Tirsdag", slots: [{ time: "07–15", name: "" }, { time: "15–23", name: "" }] },
  { day: "Onsdag", slots: [{ time: "07–15", name: "" }, { time: "15–23", name: "" }] },
  { day: "Torsdag", slots: [{ time: "07–15", name: "" }, { time: "15–23", name: "" }] },
  { day: "Fredag", slots: [{ time: "07–15", name: "" }, { time: "15–23", name: "" }] },
  { day: "Lørdag", slots: [{ time: "09–18", name: "" }] },
  { day: "Søndag", slots: [{ time: "09–18", name: "" }] },
];

const INVENTORY_CATEGORIES = [
  { name: "Pølser & Bacon", icon: "🌭", items: ["Grillpølse", "Baconpølse", "Wienerpølse", "Hamburger", "Pølsebrød fine", "Pølsebrød grove"] },
  { name: "Bakeri", icon: "🥐", items: ["Boller", "Baguetter", "Surdeigsandwich", "Tacobaguett", "Pizzaslice", "Kaker"] },
  { name: "Drikke", icon: "🥤", items: ["Cola", "Fanta", "Sprite", "Vann", "Energidrikk", "Juice", "Smoothie"] },
  { name: "Kaffe & Is", icon: "☕", items: ["Kaffebønner", "Melk", "Sukker", "Rørepinner", "Sirup", "Iskrem-mix"] },
  { name: "Snacks", icon: "🍿", items: ["Chips", "Posegodt", "Sjokolade", "Nøtter", "Tyggegummi"] },
  { name: "Kiosk & Tobakk", icon: "🏪", items: ["Røyk", "Snus", "Lightere", "Paraplyer", "Ladekabel"] },
  { name: "Forbruk", icon: "🧹", items: ["Kluter", "Mopper", "Oppvaskmiddel", "JIF Universal", "Taski", "D10", "Skurekrem", "Bolleposer", "Servietter"] },
];

const TRAINING_MODULES = [
  { id: "kasse", title: "Kassebetjening", icon: "💳", difficulty: "Grunnleggende", steps: [
    "Logg inn med din personlige kode", "Skann varer med strekkodeleser", "Manuell varesøk: trykk F2 og søk på varenavn",
    "Kontant: legg inn mottatt beløp, gi tilbake veksel", "Kort: vent til terminalen godkjenner",
    "Vipps: kunden skanner QR-koden på skjermen", "Alderskontroll: sjekk ID ved røyk, snus og alkohol",
    "Feil? Trykk Annuller (rød knapp) før kvittering printes",
  ]},
  { id: "mat", title: "Mathåndtering & Hygiene", icon: "🧤", difficulty: "Viktig", steps: [
    "Vask hendene FØR du tar i mat – alltid", "Bruk hansker ved all matlaging",
    "Temperaturkontroll: pølser >72°C, kjølevarer <4°C", "Stekeprosess boller: 180°C i 12–15 min",
    "Pizzaslice: sjekk vann i dampskap, 8 min steketid", "Datomerking: sjekk ALLTID dato før utlegging",
    "Svinn: registrer i systemet, legg i svinnbøtte", "TooGoodToGo: pakk i pose, merk med utpris 118 kr",
  ]},
  { id: "renhold", title: "Renholdsrutiner", icon: "🧽", difficulty: "Grunnleggende", steps: [
    "Glass: tørr ren klut + JIF Universal, aldri vått", "Metall: tørr ren klut + Taski, poler til blankt",
    "Highspeed: legg inn filter/skåler, kjør full syklus", "Oppvaskmaskin: bytt vann ved skift, vask filter",
    "Gulv: fei først, vask med mopp og rengjøringsmiddel", "Vasker: skurekrem, skrubb, skyll grundig",
    "Kassedisk: tørk med klut og D10 minimum 2x per vakt",
    "Kjølerom: tørk hyller, fjern tomme esker, vask gulv ukentlig",
  ]},
  { id: "sikkerhet", title: "Sikkerhet & Rutiner", icon: "🔒", difficulty: "Viktig", steps: [
    "Kassen skal ALLTID ha 2 000 kr ved vaktstart", "Kontanter over 2 000 kr → oppgjørspose → safe",
    "Aldri la kassen stå åpen uten tilsyn", "Dropp alltid på DITT navn i systemet",
    "Ran: gi fra deg alt, ikke gjør motstand, ring 112 etterpå", "Tyveri: observer, ikke konfronter, meld til sjef",
    "Brann: aktiver alarm, evakuer, ring 110", "Nødstopp strøm: rød bryter bak kassen",
  ]},
];

const ORDRE_SUPPLIERS = [
  { id:"oppe", name:"OPPE", icon:"🏪", sections: [
    { name:"🥖 Baguett", items:[
      {name:"Kokt Skinke 500g Gilde",nr:"24704",dpak:1,fpak:1,pris:124.39},
      {name:"Bøkerøkt Kyllingpålegg 250G",nr:"73528",dpak:1,fpak:12,pris:57.91},
      {name:"Kylling Salatkjøtt 500g",nr:"73316",dpak:1,fpak:10,pris:95.23},
      {name:"Salsasaus Idun 870g",nr:"67596",dpak:1,fpak:1,pris:40.91},
      {name:"Soft Flora Margarin 2kg",nr:"25667",dpak:1,fpak:2,pris:89.89},
      {name:"Hamburger Stekt 130g",nr:"29134",dpak:1,fpak:42,pris:31.15},
      {name:"Kyllingburger BBQ",nr:"71902",dpak:1,fpak:1,pris:865.76},
      {name:"Hamburgerbrød Brioche 80g",nr:"68241",dpak:1,fpak:60,pris:4.40},
    ]},
    { name:"🌭 Pølse & Pizza", items:[
      {name:"Firkantpizza Pepperoni",nr:"74767",dpak:1,fpak:10,pris:58.00},
      {name:"Firkantpizza Chili Cheese",nr:"74800",dpak:1,fpak:10,pris:54.75},
      {name:"Firkantpizza Mexicana",nr:"74798",dpak:1,fpak:10,pris:58.52},
      {name:"Lv Spesialbacon 5,04kg",nr:"23863",dpak:1,fpak:252,pris:3.94},
      {name:"Lv25 Ostepølse Fersk",nr:"72720",dpak:1,fpak:84,pris:14.81},
      {name:"Lv25 Grillpølse Fersk",nr:"72722",dpak:1,fpak:81,pris:11.87},
      {name:"Pølsebrød Potato 50g x80",nr:"63289",dpak:1,fpak:80,pris:3.51},
      {name:"Pølsebrød Grovt 60g",nr:"71274",dpak:1,fpak:80,pris:2.49},
      {name:"Hot Pepper Relish 8x250g",nr:"64826",dpak:1,fpak:8,pris:31.68},
      {name:"Pommes Fr. Cheddar Saus",nr:"69221",dpak:1,fpak:6,pris:56.23},
    ]},
    { name:"📦 Bak kasse", items:[
      {name:"WMF Presto Ren Tabl 1,3g",nr:"27581",dpak:1,fpak:100,pris:3.83},
      {name:"WMF Rengjør Melkedisp",nr:"28282",dpak:1,fpak:1,pris:885.45},
      {name:"Bakeglans 420g",nr:"24668",dpak:1,fpak:6,pris:76.65},
      {name:"Formfett 300ml",nr:"12148",dpak:1,fpak:12,pris:36.55},
      {name:"Thermorull 80x80 3pk",nr:"63638",dpak:1,fpak:3,pris:18.58},
      {name:"Knytesekk 125L Transp",nr:"68837",dpak:1,fpak:18,pris:25.96},
      {name:"7E Pølsekano",nr:"28819",dpak:1,fpak:1000,pris:0.18},
    ]},
    { name:"☕ Kaffemaskin", items:[
      {name:"7E Kaffebeger FS 30CL",nr:"74420",dpak:1,fpak:448,pris:0.87},
      {name:"Lokk 12-16oz Fib Miljø",nr:"69792",dpak:1,fpak:1200,pris:0.59},
      {name:"Oat Drink 1,5% Oatly 1L",nr:"69063",dpak:1,fpak:6,pris:20.33},
      {name:"Espresso Hel 500g",nr:"61820",dpak:1,fpak:12,pris:100.48},
      {name:"Hele Bønner Mørkbrent 500g",nr:"67160",dpak:1,fpak:12,pris:86.76},
      {name:"Sjokopulver 1kg",nr:"61821",dpak:1,fpak:10,pris:64.66},
      {name:"Barista Caramel Sirup",nr:"22428",dpak:1,fpak:1,pris:86.91},
      {name:"Barista Vanilla Sirup",nr:"24883",dpak:1,fpak:1,pris:86.91},
      {name:"Sukkerrør Brunt 3g",nr:"73377",dpak:1,fpak:1000,pris:0.32},
    ]},
  ]},
  { id:"nede", name:"NEDE", icon:"⬇️", sections: [
    { name:"🥐 Boller", items:[
      {name:"Sjokoladeboller 85g Baxt",nr:"24512",dpak:1,fpak:150,pris:3.92},
      {name:"Rosinboller 85g Baxt",nr:"24510",dpak:1,fpak:150,pris:2.48},
      {name:"Hveteboller 85g Baxt",nr:"24511",dpak:1,fpak:150,pris:2.42},
      {name:"Karamellbolle 85G Baxt",nr:"74460",dpak:1,fpak:150,pris:4.89},
      {name:"Croissant Sjokolade 100g",nr:"74196",dpak:1,fpak:60,pris:12.61},
      {name:"Croissant Plain 90g",nr:"24713",dpak:1,fpak:50,pris:10.72},
      {name:"Spandauer 90g",nr:"73072",dpak:1,fpak:48,pris:8.58},
      {name:"Kanelknute Gourmet 160g",nr:"61788",dpak:1,fpak:60,pris:11.33},
    ]},
    { name:"🍪 Kaker", items:[
      {name:"Gourmet Cookie Chocolate",nr:"66608",dpak:1,fpak:40,pris:15.89},
      {name:"Gourmet Cookie Milk Choc",nr:"72576",dpak:1,fpak:40,pris:16.04},
      {name:"Belgiske Vafler Sjokolade",nr:"19239",dpak:1,fpak:28,pris:15.26},
      {name:"Donut Filled Cream 70g",nr:"74099",dpak:1,fpak:48,pris:10.96},
      {name:"Donut Filled Choco 69g",nr:"74098",dpak:1,fpak:48,pris:10.96},
      {name:"Muffin Blueberry XXL",nr:"22463",dpak:1,fpak:16,pris:16.94},
      {name:"Muffin Triple Choco XXL",nr:"22464",dpak:1,fpak:16,pris:18.07},
      {name:"Muffin Carrot Cream Cheese",nr:"60367",dpak:1,fpak:16,pris:17.37},
    ]},
    { name:"🍔 Mat", items:[
      {name:"Samosa Vegetable",nr:"71774",dpak:1,fpak:15,pris:22.89},
      {name:"Chkn Tikka Samosa Jumbo",nr:"73447",dpak:1,fpak:15,pris:25.29},
      {name:"Hot Wings Grillet 1,5kg",nr:"71831",dpak:1,fpak:20,pris:34.93},
      {name:"Taquitos Chicken Buffalo",nr:"19222",dpak:1,fpak:48,pris:11.89},
      {name:"Taquitos Chilli Cheese",nr:"72689",dpak:1,fpak:48,pris:11.67},
      {name:"Panini Kylling & Pesto",nr:"68606",dpak:1,fpak:14,pris:32.95},
      {name:"Panini Salami & Røkt Ost",nr:"68607",dpak:1,fpak:14,pris:32.94},
      {name:"Panini Mozarella Pesto",nr:"72599",dpak:1,fpak:14,pris:32.05},
      {name:"Bagels Plain 120g",nr:"74058",dpak:1,fpak:30,pris:8.48},
    ]},
    { name:"📦 Emballasje", items:[
      {name:"Dispenserserviett",nr:"60498",dpak:1,fpak:7200,pris:0.06},
      {name:"Bakepapir 40x60cm",nr:"60901",dpak:1,fpak:1000,pris:0.70},
      {name:"7E Wrapspapir",nr:"62015",dpak:1,fpak:1000,pris:0.69},
      {name:"7E Bakepose 1kg",nr:"71856",dpak:1,fpak:500,pris:0.40},
      {name:"7E Papirbærepose",nr:"69532",dpak:1,fpak:200,pris:1.23},
      {name:"7E Pizzabrett",nr:"61655",dpak:1,fpak:1000,pris:0.65},
      {name:"Engangshanske Nitril L",nr:"71314",dpak:1,fpak:10,pris:62.72},
    ]},
    { name:"🧹 Vasketing", items:[
      {name:"Taski Sprint Spitfire Plus",nr:"72006",dpak:1,fpak:6,pris:318.12},
      {name:"Sumo Inox Stålpuss",nr:"28568",dpak:1,fpak:6,pris:92.09},
      {name:"Pep Universal 750ml",nr:"72976",dpak:1,fpak:6,pris:51.12},
      {name:"Pep Ovn & Grill 750ml",nr:"74371",dpak:1,fpak:6,pris:64.58},
      {name:"Jif Skurekrem 500ml",nr:"65469",dpak:1,fpak:12,pris:26.70},
      {name:"Suma Maskinoppv. L46 5L",nr:"28165",dpak:1,fpak:1,pris:370.92},
      {name:"Tork Håndtørk Ark",nr:"21043",dpak:1,fpak:21,pris:18.16},
      {name:"Tork Skumsåpe X Mild",nr:"29146",dpak:1,fpak:6,pris:119.67},
    ]},
  ]},
  { id:"kolly", name:"Kolly Drikke", icon:"🥤", sections: [
    { name:"🐂 Red Bull", items:[
      {name:"Red Bull Regular 0,47L",nr:"19248",dpak:1,fpak:24,pris:27.35},
      {name:"Red Bull Regular 0,35L",nr:"19247",dpak:1,fpak:24,pris:21.42},
      {name:"Red Bull Regular 0,25L",nr:"10812",dpak:1,fpak:24,pris:15.69},
      {name:"Red Bull Sugarfree 0,25L",nr:"10813",dpak:1,fpak:24,pris:15.69},
      {name:"Red Bull Zero 0,25L",nr:"72656",dpak:1,fpak:24,pris:15.27},
      {name:"Red Bull Hvit Fersken 0,25L",nr:"73266",dpak:1,fpak:24,pris:16.11},
      {name:"Red Bull Spring Edition",nr:"74647",dpak:1,fpak:24,pris:16.09},
    ]},
    { name:"💪 Nocco & Vitamin Well", items:[
      {name:"Nocco Ramonade 0,33L",nr:"67493",dpak:1,fpak:24,pris:14.88},
      {name:"Nocco Grand Sour 0,33L",nr:"72208",dpak:1,fpak:24,pris:14.95},
      {name:"Nocco Stellar Blend 0,33L",nr:"74055",dpak:1,fpak:24,pris:14.95},
      {name:"Vitamin Well Reload 0,5L",nr:"10806",dpak:1,fpak:12,pris:14.04},
      {name:"Vitamin Well Awake 0,5L",nr:"25574",dpak:1,fpak:12,pris:14.06},
      {name:"Vitamin Well Antioxidant",nr:"10804",dpak:1,fpak:12,pris:14.04},
    ]},
    { name:"🥤 Annet drikke", items:[
      {name:"Dr Pepper 0,5L",nr:"61073",dpak:1,fpak:12,pris:17.43},
      {name:"Snapple Kiwi Strawberry",nr:"29087",dpak:1,fpak:12,pris:25.52},
      {name:"Snapple Mango 473ml",nr:"29088",dpak:1,fpak:12,pris:25.52},
      {name:"San Pellegrino Limonata",nr:"66450",dpak:1,fpak:24,pris:17.20},
      {name:"Grans Taffel Stillvann 0,45L",nr:"68513",dpak:1,fpak:24,pris:7.55},
    ]},
  ]},
  { id:"ringnes", name:"Ringnes", icon:"🍋", sections: [
    { name:"🥤 Pepsi & Brus", items:[
      {name:"Pepsi Max 0,6L",nr:"74547",dpak:1,fpak:20,pris:16.19},
      {name:"Pepsi Max 0,5L",nr:"85515",dpak:1,fpak:24,pris:15.02},
      {name:"Pepsi Max Lime 0,5L",nr:"74540",dpak:1,fpak:24,pris:15.02},
      {name:"Pepsi Max Lemon 0,5L",nr:"74577",dpak:1,fpak:24,pris:15.02},
      {name:"Pepsi Max 1,5L",nr:"71024",dpak:1,fpak:8,pris:24.18},
      {name:"Solo 0,5L",nr:"85521",dpak:1,fpak:24,pris:15.02},
      {name:"Solo Super 0,5L",nr:"85522",dpak:1,fpak:24,pris:15.02},
      {name:"Mountain Dew 0,5L",nr:"85520",dpak:1,fpak:24,pris:15.27},
    ]},
    { name:"💧 Vann & Te", items:[
      {name:"Farris Lime 0,5L",nr:"71202",dpak:1,fpak:24,pris:13.33},
      {name:"Farris Naturell 0,5L",nr:"85523",dpak:1,fpak:24,pris:13.33},
      {name:"Farris Frus Bringebær",nr:"74551",dpak:1,fpak:24,pris:14.56},
      {name:"Imsdal 0,5L",nr:"85516",dpak:1,fpak:24,pris:13.02},
      {name:"Imsdal 0,65L",nr:"85517",dpak:1,fpak:20,pris:17.02},
      {name:"Imsdal 1,5L",nr:"74529",dpak:1,fpak:6,pris:17.95},
      {name:"Lipton Ice Tea Peach",nr:"74765",dpak:1,fpak:24,pris:18.68},
      {name:"Lipton Ice Tea Lemon",nr:"74766",dpak:1,fpak:24,pris:18.68},
    ]},
    { name:"⚡ Battery & Energi", items:[
      {name:"Battery Fresh 0,5L",nr:"71211",dpak:1,fpak:24,pris:14.51},
      {name:"Battery Energy Drink 0,5L",nr:"71201",dpak:1,fpak:24,pris:14.51},
      {name:"Battery Blueberry 0,5L",nr:"71210",dpak:1,fpak:24,pris:14.51},
      {name:"Battery No Cal 0,5L",nr:"71200",dpak:1,fpak:24,pris:14.51},
      {name:"Gatorade Cool Blue 0,5L",nr:"73497",dpak:1,fpak:12,pris:14.49},
    ]},
  ]},
  { id:"tine", name:"TINE Handel", icon:"🥛", sections: [
    { name:"☕ IsKaffe", items:[
      {name:"IsKaffe Cappuccino 330ml",nr:"381",dpak:1,fpak:12,pris:13.78},
      {name:"IsKaffe Mocha 330ml",nr:"382",dpak:1,fpak:12,pris:13.77},
      {name:"IsKaffe Protein Latte 330ml",nr:"7229",dpak:1,fpak:12,pris:15.83},
      {name:"IsKaffe Salty Caramel 330ml",nr:"6680",dpak:1,fpak:12,pris:13.93},
      {name:"IsKaffe Cappuccino UTEN",nr:"5856",dpak:1,fpak:12,pris:13.78},
      {name:"IsKaffe Latte UTEN 330ml",nr:"5562",dpak:1,fpak:12,pris:13.77},
    ]},
    { name:"🥛 Litago & Melk", items:[
      {name:"Litago Sjokolademelk 0,5L",nr:"262",dpak:1,fpak:10,pris:13.95},
      {name:"Litago Jordbærsmak 0,5L",nr:"266",dpak:1,fpak:10,pris:14.06},
      {name:"Litago Sjoko UTEN 0,5L",nr:"6619",dpak:1,fpak:10,pris:14.07},
      {name:"Litago Sjoko & Banan 0,5L",nr:"3654",dpak:1,fpak:10,pris:15.34},
      {name:"Sjokomelk 0,25L",nr:"3515",dpak:1,fpak:18,pris:7.56},
      {name:"Lettmelk 1,0% 1L",nr:"164",dpak:1,fpak:10,pris:15.47},
    ]},
    { name:"🏋️ YT Protein", items:[
      {name:"YT Restitusjon Kakao 330ml",nr:"426",dpak:1,fpak:12,pris:16.11},
      {name:"YT Restitusjon Banan/Jordbær",nr:"425",dpak:1,fpak:12,pris:16.11},
      {name:"YT Restitusjon Kakao PRO",nr:"5554",dpak:1,fpak:12,pris:20.83},
      {name:"YT Proteinshake Sjoko UTEN",nr:"7237",dpak:1,fpak:12,pris:16.51},
      {name:"YT Proteinpudding Sjoko",nr:"6184",dpak:1,fpak:10,pris:16.77},
      {name:"YT Proteinpudding Vanilje",nr:"6464",dpak:1,fpak:10,pris:16.77},
    ]},
    { name:"🧀 Ost & Yoghurt", items:[
      {name:"Go'morgen Skogsbær 190g",nr:"6820",dpak:1,fpak:6,pris:10.23},
      {name:"Go'morgen Vanilje/Nøtter",nr:"6825",dpak:1,fpak:6,pris:13.01},
      {name:"Go'morgen Jordbær 190g",nr:"6821",dpak:1,fpak:6,pris:10.23},
      {name:"Norvegia Hotellbrett 600g",nr:"1495",dpak:1,fpak:5,pris:88.86},
      {name:"Cheddar Skivet Hotellbrett",nr:"7296",dpak:1,fpak:5,pris:87.44},
      {name:"Kremgo Naturell 1kg Spann",nr:"2315",dpak:1,fpak:2,pris:144.29},
    ]},
  ]},
  { id:"diplom", name:"Diplom IS", icon:"🍦", sections: [
    { name:"🍦 Is", items:[
      {name:"Royal Tropisk 90ml",nr:"74502",dpak:1,fpak:16,pris:15.86},
      {name:"Royal Peanøtt Salt Karam",nr:"74509",dpak:1,fpak:20,pris:14.15},
      {name:"Royal Trippel",nr:"65487",dpak:1,fpak:16,pris:14.58},
      {name:"Royal Pistasj",nr:"65486",dpak:1,fpak:16,pris:16.17},
      {name:"Royal Magi UTZ MB",nr:"65480",dpak:1,fpak:16,pris:16.37},
      {name:"Gigant Salt Karamell 240ml",nr:"74504",dpak:1,fpak:8,pris:21.15},
      {name:"Gullpinne",nr:"65465",dpak:1,fpak:20,pris:11.78},
      {name:"Gullpinne Pistasj 90ml",nr:"74506",dpak:1,fpak:20,pris:12.82},
      {name:"Kjempeyes 20stk",nr:"71949",dpak:1,fpak:20,pris:10.66},
      {name:"Krone-Is Sjokolade",nr:"66815",dpak:1,fpak:18,pris:10.28},
      {name:"Krone-Is Jordbær",nr:"65466",dpak:1,fpak:18,pris:10.26},
      {name:"Sandwich Original",nr:"65489",dpak:1,fpak:35,pris:11.05},
      {name:"Lion King Size",nr:"65474",dpak:1,fpak:8,pris:20.50},
    ]},
  ]},
  { id:"bama", name:"Bama Storkjøkken", icon:"🥬", sections: [
    { name:"🥬 Ferskvarer", items:[
      {name:"Street Sandwich Egg & Bacon",nr:"",dpak:1,fpak:32,pris:36.21},
      {name:"Onigiri Tuna Mayo",nr:"",dpak:1,fpak:6,pris:37.00},
      {name:"Onigiri Chicken",nr:"",dpak:1,fpak:6,pris:37.00},
      {name:"Bacon Stekt 43% 500g",nr:"",dpak:1,fpak:6,pris:39.46},
      {name:"Ruccula Vasket 250g",nr:"",dpak:1,fpak:4,pris:14.54},
      {name:"Crispi Salat 500g",nr:"",dpak:1,fpak:6,pris:14.42},
      {name:"Spinat 250g",nr:"",dpak:1,fpak:4,pris:8.73},
      {name:"Paprika Rød 1kg",nr:"",dpak:1,fpak:9,pris:7.89},
      {name:"Tomat Import",nr:"",dpak:1,fpak:6,pris:8.46},
      {name:"Rødløk 1kg",nr:"",dpak:1,fpak:14,pris:1.91},
      {name:"Banan Dole 5kg",nr:"",dpak:1,fpak:5,pris:5.44},
    ]},
  ]},
];

// ─── ICONS ───────────────────────────────────────────────────────────
const NavIcons = {
  hjem: (a) => <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke={a ? "var(--accent-green)" : "var(--text-muted)"} strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>,
  sjekk: (a) => <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke={a ? "var(--accent-green)" : "var(--text-muted)"} strokeWidth="2" strokeLinecap="round"><path d="M9 11l3 3L22 4"/><path d="M21 12v7a2 2 0 01-2 2H5a2 2 0 01-2-2V5a2 2 0 012-2h11"/></svg>,
  vakt: (a) => <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke={a ? "var(--accent-green)" : "var(--text-muted)"} strokeWidth="2" strokeLinecap="round"><rect x="3" y="4" width="18" height="18" rx="2"/><path d="M16 2v4M8 2v4M3 10h18"/></svg>,
  varer: (a) => <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke={a ? "var(--accent-green)" : "var(--text-muted)"} strokeWidth="2" strokeLinecap="round"><path d="M6 2L3 6v14a2 2 0 002 2h14a2 2 0 002-2V6l-3-4z"/><path d="M3 6h18M16 10a4 4 0 01-8 0"/></svg>,
  rapport: (a) => <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke={a ? "var(--accent-green)" : "var(--text-muted)"} strokeWidth="2" strokeLinecap="round"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8z"/><path d="M14 2v6h6M16 13H8M16 17H8M10 9H8"/></svg>,
  laering: (a) => <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke={a ? "var(--accent-green)" : "var(--text-muted)"} strokeWidth="2" strokeLinecap="round"><path d="M2 3h6a4 4 0 014 4v14a3 3 0 00-3-3H2z"/><path d="M22 3h-6a4 4 0 00-4 4v14a3 3 0 013-3h7z"/></svg>,
  ordre: (a) => <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke={a ? "var(--accent-green)" : "var(--text-muted)"} strokeWidth="2" strokeLinecap="round"><path d="M21 16V8a2 2 0 00-1-1.73l-7-4a2 2 0 00-2 0l-7 4A2 2 0 003 8v8a2 2 0 001 1.73l7 4a2 2 0 002 0l7-4A2 2 0 0021 16z"/><path d="M3.27 6.96L12 12.01l8.73-5.05M12 22.08V12"/></svg>,
  chat: (a) => <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke={a ? "var(--accent-green)" : "var(--text-muted)"} strokeWidth="2" strokeLinecap="round"><path d="M21 15a2 2 0 01-2 2H7l-4 4V5a2 2 0 012-2h14a2 2 0 012 2z"/></svg>,
};

// ─── COMPONENTS ──────────────────────────────────────────────────────
function ProgressRing({ percent, size = 56 }) {
  const r = (size - 6) / 2, circ = 2 * Math.PI * r;
  return (
    <svg width={size} height={size} style={{ transform: "rotate(-90deg)" }}>
      <circle cx={size/2} cy={size/2} r={r} fill="none" stroke="var(--ring-bg)" strokeWidth="5"/>
      <circle cx={size/2} cy={size/2} r={r} fill="none"
        stroke={percent===100?"var(--accent-green)":"var(--accent-orange)"}
        strokeWidth="5" strokeLinecap="round"
        strokeDasharray={circ} strokeDashoffset={circ-(percent/100)*circ}
        style={{ transition: "stroke-dashoffset 0.5s ease, stroke 0.3s" }}/>
    </svg>
  );
}

function TaskItem({ task, checked, onToggle }) {
  return (
    <button onClick={onToggle} style={{
      display:"flex", alignItems:"flex-start", gap:"12px", width:"100%", padding:"12px 14px",
      border:"none", background: checked?"var(--task-done-bg)":"var(--task-bg)",
      borderRadius:"10px", cursor:"pointer", textAlign:"left", transition:"all 0.2s",
      borderLeft: task.note?"3px solid var(--accent-orange)":"3px solid transparent",
    }}>
      <div style={{
        width:"22px", height:"22px", borderRadius:"6px", flexShrink:0, marginTop:"1px",
        border: checked?"none":"2px solid var(--check-border)",
        background: checked?"var(--accent-green)":"transparent",
        display:"flex", alignItems:"center", justifyContent:"center", transition:"all 0.2s",
      }}>
        {checked && <svg width="13" height="13" viewBox="0 0 14 14" fill="none"><path d="M2.5 7.5L5.5 10.5L11.5 3.5" stroke="#fff" strokeWidth="2.2" strokeLinecap="round"/></svg>}
      </div>
      <div style={{ flex:1 }}>
        <div style={{ fontSize:"14px", fontWeight:500, lineHeight:1.4, color: checked?"var(--text-done)":"var(--text-primary)", textDecoration: checked?"line-through":"none" }}>
          {task.task}
        </div>
        {task.note && <div style={{ fontSize:"11.5px", color:"var(--accent-orange)", marginTop:"3px", fontWeight:600 }}>⚡ {task.note}</div>}
      </div>
    </button>
  );
}

// ─── PAGES ───────────────────────────────────────────────────────────
function ChecklistPage({ checked, setChecked }) {
  const [activeList, setActiveList] = useState("apning");
  const [collapsed, setCollapsed] = useState({});
  const list = CHECKLISTS[activeList];
  const total = list.sections.reduce((a,s)=>a+s.tasks.length,0);
  const done = list.sections.reduce((a,s)=>a+s.tasks.filter(t=>checked[activeList]?.[t.id]).length,0);
  const pct = total?Math.round((done/total)*100):0;

  const toggle = id => setChecked(p=>({...p,[activeList]:{...p[activeList],[id]:!p[activeList]?.[id]}}));
  const isExp = i => collapsed[`${activeList}-${i}`] !== false;

  return (
    <div>
      <div style={{ display:"flex", gap:"5px", marginBottom:"16px" }}>
        {Object.entries(CHECKLISTS).map(([k,l])=>{
          const active=activeList===k;
          const t=l.sections.reduce((a,s)=>a+s.tasks.length,0);
          const d=l.sections.reduce((a,s)=>a+s.tasks.filter(x=>checked[k]?.[x.id]).length,0);
          return (
            <button key={k} onClick={()=>setActiveList(k)} style={{
              flex:1, padding:"10px 4px", borderRadius:"10px", border:"none",
              background:active?"var(--accent-green)":"var(--surface)", color:active?"#0C0F0A":"var(--text-secondary)",
              fontSize:"12px", fontWeight:700, cursor:"pointer", display:"flex", flexDirection:"column", alignItems:"center", gap:"2px",
            }}>
              <span>{l.icon} {l.title.split(" ")[0]}</span>
              <span style={{ fontSize:"10px", opacity:0.7, fontFamily:"monospace" }}>{d}/{t}</span>
            </button>
          );
        })}
      </div>
      <div style={{ display:"flex", alignItems:"center", justifyContent:"space-between", marginBottom:"14px" }}>
        <div style={{ display:"flex", alignItems:"center", gap:"12px" }}>
          <div style={{ position:"relative" }}>
            <ProgressRing percent={pct} size={48}/>
            <div style={{ position:"absolute", inset:0, display:"flex", alignItems:"center", justifyContent:"center", fontSize:"13px", fontWeight:700, color:pct===100?"var(--accent-green)":"var(--text-primary)", fontFamily:"monospace" }}>{pct}%</div>
          </div>
          <div>
            <div style={{ fontSize:"16px", fontWeight:700, color:"var(--text-primary)" }}>{list.title}</div>
            <div style={{ fontSize:"12px", color:"var(--text-muted)" }}>{done} av {total} ferdig</div>
          </div>
        </div>
        {done>0 && <button onClick={()=>setChecked(p=>({...p,[activeList]:{}}))} style={{ fontSize:"11px", color:"var(--accent-red)", background:"rgba(238,39,55,0.08)", border:"1px solid rgba(239,68,68,0.2)", borderRadius:"8px", padding:"5px 10px", cursor:"pointer", fontWeight:600 }}>Nullstill</button>}
      </div>
      {list.sections.map((sec,si)=>{
        const sd=sec.tasks.filter(t=>checked[activeList]?.[t.id]).length;
        const exp=isExp(si);
        return (
          <div key={si} style={{ marginBottom:"8px", background:"var(--surface)", borderRadius:"14px", border: sd===sec.tasks.length?"1px solid var(--divider)":"1px solid var(--divider)", overflow:"hidden" }}>
            <button onClick={()=>setCollapsed(p=>({...p,[`${activeList}-${si}`]:exp?false:true}))} style={{
              width:"100%", display:"flex", alignItems:"center", justifyContent:"space-between",
              padding:"12px 16px", background:"none", border:"none", cursor:"pointer",
            }}>
              <span style={{ fontSize:"12px", fontWeight:700, letterSpacing:"0.04em", textTransform:"uppercase", color:sd===sec.tasks.length?"var(--accent-green)":"var(--text-secondary)" }}>
                {sd===sec.tasks.length&&"✅ "}{sec.title}
              </span>
              <span style={{ fontSize:"11px", fontFamily:"monospace", color:"var(--text-muted)" }}>{sd}/{sec.tasks.length} {exp?"▾":"▸"}</span>
            </button>
            {exp && <div style={{ display:"flex", flexDirection:"column", gap:"5px", padding:"0 8px 10px" }}>
              {sec.tasks.map(t=><TaskItem key={t.id} task={t} checked={!!checked[activeList]?.[t.id]} onToggle={()=>toggle(t.id)}/>)}
            </div>}
          </div>
        );
      })}
    </div>
  );
}

function TidPage() {
  const [tab, setTab] = useState("plan");
  const [dateOffset, setDateOffset] = useState(0);
  const TIDSBANKEN_URL = "https://min.tidsbanken.net/hjem?key=e1b88004-8551-47bc-9e38-fc050fb2c964";

  const today = new Date();
  const viewDate = new Date(today); viewDate.setDate(today.getDate() + dateOffset);
  const dayName = viewDate.toLocaleDateString("nb-NO",{weekday:"long"});
  const dateStr = viewDate.toLocaleDateString("nb-NO",{day:"2-digit",month:"2-digit",year:"numeric"});
  const isToday = dateOffset === 0;

  const WORK_TYPES = [
    { id:105, name:"Natt Olav Kyrres gate", short:"Natt", color:"#1a3a5c", textColor:"#fff" },
    { id:100, name:"Ordinærvakt", short:"Ordinær", color:"#2563eb", textColor:"#fff" },
    { id:102, name:"Tidlig Olav Kyrres gate", short:"Tidlig", color:"#0d9488", textColor:"#fff" },
    { id:104, name:"Kveld Olav Kyrres gate", short:"Kveld", color:"#16a34a", textColor:"#fff" },
    { id:103, name:"Midtvakt Olav Kyrres gate", short:"Midtvakt", color:"#7c3aed", textColor:"#fff" },
    { id:131, name:"Ferie", short:"Ferie", color:"#dc2626", textColor:"#fff" },
  ];

  const EMPLOYEES = [
    { id:"12", name:"Jatharthan Muthulingam" },
    { id:"1001", name:"Yousef Ahmad" },
    { id:"20117", name:"Christine Joy Daria" },
    { id:"501256", name:"Shahad Dawood Al-Obaidi" },
    { id:"501804", name:"Nathan Mpoyi" },
    { id:"502269", name:"Zabiullah Sanwari" },
    { id:"503213", name:"Mansoor Redi" },
    { id:"507884", name:"Emil Hennaen Linder" },
  ];

  const [planned, setPlanned] = useState([
    { typeId:105, fra:"23:59", til:"07:00", timer:7.02, ansattId:"12" },
    { typeId:100, fra:"15:15", til:"23:00", timer:7.75, ansattId:"12" },
    { typeId:102, fra:"07:00", til:"15:00", timer:8.00, ansattId:"1001" },
    { typeId:104, fra:"17:00", til:"00:00", timer:7.00, ansattId:"20117" },
    { typeId:131, fra:"00:00", til:"00:00", timer:0.00, ansattId:null },
    { typeId:103, fra:"12:00", til:"19:00", timer:7.00, ansattId:"503213" },
    { typeId:131, fra:"00:00", til:"00:00", timer:0.00, ansattId:null },
  ]);

  const [timesheet, setTimesheet] = useState([
    { ansattId:"12", typeId:100, fra:"15:15", til:"23:50", timer:8.58, avvik:-6.15, lonnart:"10 Timelønn", avdeling:"7 Jernbanestasjonen" },
    { ansattId:"12", typeId:100, fra:"15:15", til:"23:50", timer:8.58, avvik:0, lonnart:"905 Tillegg Søndag", avdeling:"7 Jernbanestasjonen" },
    { ansattId:"1001", typeId:102, fra:"07:00", til:"15:00", timer:8.00, avvik:0, lonnart:"10 Timelønn", avdeling:"2 Olav Kyrres gate" },
    { ansattId:"503213", typeId:103, fra:"12:43", til:"19:33", timer:6.83, avvik:-0.17, lonnart:"10 Timelønn", avdeling:"2 Olav Kyrres gate" },
  ]);

  const getType = (id) => WORK_TYPES.find(t=>t.id===id) || WORK_TYPES[0];
  const getEmp = (id) => EMPLOYEES.find(e=>e.id===id);
  const sumPlanned = planned.reduce((a,p)=>a+p.timer,0);
  const sumActual = timesheet.reduce((a,t)=>a+t.timer,0);
  const sumAvvik = timesheet.reduce((a,t)=>a+t.avvik,0);

  // Sum per arbeidstype
  const sumByType = {};
  timesheet.forEach(t => {
    const type = getType(t.typeId);
    if (!sumByType[type.name]) sumByType[type.name] = { timer: 0, subs: {} };
    sumByType[type.name].timer += t.timer;
    if (!sumByType[type.name].subs[t.lonnart]) sumByType[type.name].subs[t.lonnart] = 0;
    sumByType[type.name].subs[t.lonnart] += t.timer;
  });

  // Sum per lønnsart
  const sumByLonn = {};
  timesheet.forEach(t => {
    if (!sumByLonn[t.lonnart]) sumByLonn[t.lonnart] = 0;
    sumByLonn[t.lonnart] += t.timer;
  });

  const TypeBadge = ({typeId, small}) => {
    const type = getType(typeId);
    return <span style={{ background:type.color, color:type.textColor, fontSize: small?"9px":"10px", fontWeight:700, padding: small?"2px 6px":"3px 8px", borderRadius:"4px", whiteSpace:"nowrap" }}>{small ? type.short : type.name}</span>;
  };

  return (
    <div>
      {/* Tidsbanken Link */}
      <a href={TIDSBANKEN_URL} target="_blank" rel="noopener noreferrer" style={{
        display:"flex", alignItems:"center", justifyContent:"space-between", padding:"10px 14px",
        background:"#FFFFFF", borderRadius:"12px", boxShadow:"0 2px 8px rgba(0,0,0,0.06)",
        border:"1px solid rgba(0,135,81,0.15)", textDecoration:"none", marginBottom:"12px",
      }}>
        <div style={{ display:"flex", alignItems:"center", gap:"8px" }}>
          <span style={{ fontSize:"18px" }}>⏱</span>
          <div>
            <div style={{ fontSize:"13px", fontWeight:700, color:"var(--text-primary)" }}>Åpne Tidsbanken</div>
            <div style={{ fontSize:"10px", color:"var(--text-muted)" }}>Offisiell stempling og timeliste</div>
          </div>
        </div>
        <span style={{ fontSize:"12px", color:"var(--accent-green)", fontWeight:700 }}>→</span>
      </a>

      {/* Date nav + avdeling */}
      <div style={{ background:"var(--surface)", borderRadius:"12px", padding:"10px 12px", border:"1px solid var(--divider)", marginBottom:"12px" }}>
        <div style={{ fontSize:"10px", color:"var(--accent-green)", fontWeight:600, marginBottom:"6px" }}>📍 2 Olav Kyrres gate</div>
        <div style={{ display:"flex", alignItems:"center", justifyContent:"space-between" }}>
          <button onClick={()=>setDateOffset(d=>d-1)} style={{ background:"var(--task-bg)", border:"1px solid var(--divider)", borderRadius:"6px", padding:"4px 10px", color:"var(--text-secondary)", cursor:"pointer", fontSize:"14px" }}>←</button>
          <div style={{ textAlign:"center" }}>
            <div style={{ fontSize:"14px", fontWeight:700, color:"var(--text-primary)", textTransform:"capitalize" }}>{dayName} {dateStr}</div>
            {!isToday && <button onClick={()=>setDateOffset(0)} style={{ fontSize:"10px", color:"var(--accent-green)", background:"none", border:"none", cursor:"pointer", fontWeight:600 }}>→ I dag</button>}
          </div>
          <button onClick={()=>setDateOffset(d=>d+1)} style={{ background:"var(--task-bg)", border:"1px solid var(--divider)", borderRadius:"6px", padding:"4px 10px", color:"var(--text-secondary)", cursor:"pointer", fontSize:"14px" }}>→</button>
        </div>
      </div>

      {/* Tabs */}
      <div style={{ display:"flex", gap:"3px", marginBottom:"12px" }}>
        {[{k:"plan",l:"📋 Planlagt"},{k:"time",l:"⏱ Timeliste"},{k:"ansatt",l:"👥 Ansatte"},{k:"sum",l:"📊 Sum"}].map(t => (
          <button key={t.k} onClick={()=>setTab(t.k)} style={{
            flex:1, padding:"8px 2px", borderRadius:"8px", border:"none", fontSize:"10.5px", fontWeight:700, cursor:"pointer",
            background: tab===t.k?"var(--accent-green)":"var(--surface)", color: tab===t.k?"#0C0F0A":"var(--text-muted)",
          }}>{t.l}</button>
        ))}
      </div>

      {/* PLANLAGT */}
      {tab === "plan" && (
        <div>
          <div style={{ display:"flex", justifyContent:"space-between", marginBottom:"8px" }}>
            <span style={{ fontSize:"12px", fontWeight:700, color:"var(--text-secondary)" }}>PLANLAGTE VAKTER</span>
            <span style={{ fontSize:"12px", fontWeight:700, color:"var(--accent-green)", fontFamily:"monospace" }}>Sum: {sumPlanned.toFixed(2)}t</span>
          </div>
          <div style={{ display:"flex", flexDirection:"column", gap:"5px" }}>
            {planned.map((p,i) => {
              const type = getType(p.typeId);
              const emp = p.ansattId ? getEmp(p.ansattId) : null;
              return (
                <div key={i} style={{ background:"var(--surface)", borderRadius:"10px", padding:"10px 12px", border:"1px solid var(--divider)", borderLeft:`4px solid ${type.color}` }}>
                  <div style={{ display:"flex", alignItems:"center", justifyContent:"space-between", marginBottom:"4px" }}>
                    <TypeBadge typeId={p.typeId}/>
                    <span style={{ fontSize:"14px", fontWeight:700, color:"var(--text-primary)", fontFamily:"monospace" }}>{p.timer.toFixed(2)}t</span>
                  </div>
                  <div style={{ display:"flex", alignItems:"center", justifyContent:"space-between" }}>
                    <span style={{ fontSize:"12px", color:"var(--text-muted)", fontFamily:"monospace" }}>{p.fra} → {p.til}</span>
                    {emp && <span style={{ fontSize:"11px", color:"var(--text-secondary)" }}>{emp.name}</span>}
                  </div>
                </div>
              );
            })}
          </div>
        </div>
      )}

      {/* TIMELISTE */}
      {tab === "time" && (
        <div>
          <div style={{ display:"flex", justifyContent:"space-between", marginBottom:"8px" }}>
            <span style={{ fontSize:"12px", fontWeight:700, color:"var(--text-secondary)" }}>TIMELISTE</span>
            <div style={{ display:"flex", gap:"10px" }}>
              <span style={{ fontSize:"11px", color:"var(--accent-green)", fontFamily:"monospace" }}>{sumActual.toFixed(2)}t</span>
              <span style={{ fontSize:"11px", color: sumAvvik<0?"var(--accent-red)":"var(--accent-green)", fontFamily:"monospace" }}>{sumAvvik>=0?"+":""}{sumAvvik.toFixed(2)}</span>
            </div>
          </div>
          <div style={{ display:"flex", flexDirection:"column", gap:"5px" }}>
            {timesheet.map((t,i) => {
              const type = getType(t.typeId);
              const emp = getEmp(t.ansattId);
              return (
                <div key={i} style={{ background:"var(--surface)", borderRadius:"10px", padding:"10px 12px", border:"1px solid var(--divider)", borderLeft:`4px solid ${type.color}` }}>
                  <div style={{ display:"flex", alignItems:"center", justifyContent:"space-between", marginBottom:"6px" }}>
                    <div style={{ display:"flex", alignItems:"center", gap:"6px" }}>
                      <TypeBadge typeId={t.typeId} small/>
                      {emp && <span style={{ fontSize:"12px", color:"var(--text-primary)", fontWeight:600 }}>{emp.name.split(" ")[0]}</span>}
                    </div>
                  </div>
                  <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr 1fr 1fr", gap:"4px" }}>
                    <div>
                      <div style={{ fontSize:"9px", color:"var(--text-muted)" }}>Fra</div>
                      <div style={{ fontSize:"13px", fontWeight:700, color:"var(--text-primary)", fontFamily:"monospace" }}>{t.fra}</div>
                    </div>
                    <div>
                      <div style={{ fontSize:"9px", color:"var(--text-muted)" }}>Til</div>
                      <div style={{ fontSize:"13px", fontWeight:700, color:"var(--text-primary)", fontFamily:"monospace" }}>{t.til}</div>
                    </div>
                    <div>
                      <div style={{ fontSize:"9px", color:"var(--text-muted)" }}>Timer</div>
                      <div style={{ fontSize:"13px", fontWeight:700, color:"var(--accent-green)", fontFamily:"monospace" }}>{t.timer.toFixed(2)}</div>
                    </div>
                    <div>
                      <div style={{ fontSize:"9px", color:"var(--text-muted)" }}>Avvik</div>
                      <div style={{ fontSize:"13px", fontWeight:700, color: t.avvik<0?"var(--accent-red)":t.avvik>0?"var(--accent-orange)":"var(--text-muted)", fontFamily:"monospace" }}>{t.avvik!==0?(t.avvik>0?"+":"")+t.avvik.toFixed(2):"0.00"}</div>
                    </div>
                  </div>
                  <div style={{ display:"flex", justifyContent:"space-between", marginTop:"4px" }}>
                    <span style={{ fontSize:"10px", color:"var(--accent-orange)" }}>{t.lonnart}</span>
                    <span style={{ fontSize:"10px", color:"var(--text-muted)" }}>{t.avdeling}</span>
                  </div>
                </div>
              );
            })}
          </div>
        </div>
      )}

      {/* ANSATTE */}
      {tab === "ansatt" && (
        <div>
          <div style={{ fontSize:"12px", fontWeight:700, color:"var(--text-secondary)", marginBottom:"8px" }}>ANSATTE ({EMPLOYEES.length})</div>
          <div style={{ display:"flex", flexDirection:"column", gap:"4px" }}>
            {EMPLOYEES.map((emp,i) => {
              const empShifts = planned.filter(p=>p.ansattId===emp.id);
              const empTime = timesheet.filter(t=>t.ansattId===emp.id);
              const totalHours = empTime.reduce((a,t)=>a+t.timer,0);
              return (
                <div key={i} style={{ background:"var(--surface)", borderRadius:"10px", padding:"10px 14px", border:"1px solid var(--divider)", display:"flex", alignItems:"center", justifyContent:"space-between" }}>
                  <div style={{ display:"flex", alignItems:"center", gap:"10px" }}>
                    <div style={{ width:"34px", height:"34px", borderRadius:"50%", background:"var(--task-bg)", border:"1px solid var(--divider)", display:"flex", alignItems:"center", justifyContent:"center", fontSize:"12px", fontWeight:700, color:"var(--text-secondary)" }}>
                      {emp.name.split(" ").map(n=>n[0]).join("").slice(0,2)}
                    </div>
                    <div>
                      <div style={{ fontSize:"13px", fontWeight:600, color:"var(--text-primary)" }}>{emp.name}</div>
                      <div style={{ fontSize:"10px", color:"var(--text-muted)", fontFamily:"monospace" }}>#{emp.id}</div>
                    </div>
                  </div>
                  <div style={{ textAlign:"right" }}>
                    {empShifts.length > 0 && (
                      <div style={{ display:"flex", gap:"3px", justifyContent:"flex-end", marginBottom:"2px" }}>
                        {empShifts.map((s,si) => <TypeBadge key={si} typeId={s.typeId} small/>)}
                      </div>
                    )}
                    {totalHours > 0 ? (
                      <div style={{ fontSize:"13px", fontWeight:700, color:"var(--accent-green)", fontFamily:"monospace" }}>{totalHours.toFixed(2)}t</div>
                    ) : (
                      <div style={{ fontSize:"11px", color:"var(--text-muted)" }}>Ikke stemplet</div>
                    )}
                  </div>
                </div>
              );
            })}
          </div>
        </div>
      )}

      {/* SUM */}
      {tab === "sum" && (
        <div>
          {/* Sum per arbeidstype */}
          <div style={{ background:"var(--surface)", borderRadius:"12px", border:"1px solid var(--divider)", overflow:"hidden", marginBottom:"12px" }}>
            <div style={{ padding:"10px 14px", borderBottom:"1px solid var(--divider)" }}>
              <span style={{ fontSize:"12px", fontWeight:700, color:"var(--text-secondary)" }}>SUM TIMER PR ARBEIDSTYPE</span>
            </div>
            {Object.entries(sumByType).map(([name, data], i) => (
              <div key={i} style={{ borderBottom:"1px solid var(--divider)" }}>
                <div style={{ display:"flex", justifyContent:"space-between", padding:"10px 14px", background:"var(--task-bg)" }}>
                  <span style={{ fontSize:"13px", fontWeight:700, color:"var(--text-primary)" }}>{name}</span>
                  <span style={{ fontSize:"13px", fontWeight:700, color:"var(--accent-green)", fontFamily:"monospace" }}>{data.timer.toFixed(2)}</span>
                </div>
                {Object.entries(data.subs).map(([sub, hours], si) => (
                  <div key={si} style={{ display:"flex", justifyContent:"space-between", padding:"6px 14px 6px 30px" }}>
                    <span style={{ fontSize:"12px", color:"var(--text-muted)" }}>↳ {sub}</span>
                    <span style={{ fontSize:"12px", color:"var(--text-secondary)", fontFamily:"monospace" }}>{hours.toFixed(2)}</span>
                  </div>
                ))}
              </div>
            ))}
          </div>

          {/* Sum per lønnsart */}
          <div style={{ background:"var(--surface)", borderRadius:"12px", border:"1px solid var(--divider)", overflow:"hidden" }}>
            <div style={{ padding:"10px 14px", borderBottom:"1px solid var(--divider)" }}>
              <span style={{ fontSize:"12px", fontWeight:700, color:"var(--text-secondary)" }}>SUM TIMER PR LØNNSART</span>
            </div>
            {Object.entries(sumByLonn).map(([name, hours], i) => (
              <div key={i} style={{ display:"flex", justifyContent:"space-between", padding:"10px 14px", borderBottom:"1px solid var(--divider)" }}>
                <span style={{ fontSize:"13px", fontWeight:600, color:"var(--text-primary)" }}>{name}</span>
                <span style={{ fontSize:"13px", fontWeight:700, color:"var(--accent-green)", fontFamily:"monospace" }}>{hours.toFixed(2)}</span>
              </div>
            ))}
            <div style={{ display:"flex", justifyContent:"space-between", padding:"10px 14px", background:"var(--task-bg)" }}>
              <span style={{ fontSize:"13px", fontWeight:700, color:"var(--text-primary)" }}>Totalt</span>
              <span style={{ fontSize:"14px", fontWeight:800, color:"var(--accent-green)", fontFamily:"monospace" }}>{sumActual.toFixed(2)}</span>
            </div>
          </div>

          {/* Avvik */}
          <div style={{ background: sumAvvik<0?"rgba(239,68,68,0.08)":"rgba(74,222,111,0.08)", borderRadius:"12px", padding:"14px", border:`1px solid ${sumAvvik<0?"rgba(239,68,68,0.2)":"rgba(0,135,81,0.15)"}`, marginTop:"12px", textAlign:"center" }}>
            <div style={{ fontSize:"11px", color:"var(--text-muted)", marginBottom:"4px" }}>Totalt avvik fra planlagt</div>
            <div style={{ fontSize:"24px", fontWeight:800, fontFamily:"monospace", color: sumAvvik<0?"var(--accent-red)":"var(--accent-green)" }}>{sumAvvik>=0?"+":""}{sumAvvik.toFixed(2)} timer</div>
            <div style={{ fontSize:"11px", color:"var(--text-muted)", marginTop:"4px" }}>Planlagt: {sumPlanned.toFixed(2)}t · Faktisk: {sumActual.toFixed(2)}t</div>
          </div>
        </div>
      )}
    </div>
  );
}

function InventoryPage() {
  const [counts, setCounts] = useState({});
  const [activeCat, setActiveCat] = useState(0);
  const cat = INVENTORY_CATEGORIES[activeCat];

  const setCount = (item, val) => setCounts(p => ({...p, [`${activeCat}-${item}`]: Math.max(0, val)}));
  const getCount = (item) => counts[`${activeCat}-${item}`] || 0;
  const totalItems = INVENTORY_CATEGORIES.reduce((a,c) => a + c.items.filter(i => counts[`${INVENTORY_CATEGORIES.indexOf(c)}-${i}`] > 0).length, 0);

  return (
    <div>
      <div style={{ display:"flex", alignItems:"center", justifyContent:"space-between", marginBottom:"14px" }}>
        <div style={{ fontSize:"12px", color:"var(--text-muted)" }}>{totalItems} varer registrert</div>
        {totalItems>0 && <button onClick={()=>setCounts({})} style={{ fontSize:"11px", color:"var(--accent-red)", background:"rgba(238,39,55,0.08)", border:"1px solid rgba(239,68,68,0.2)", borderRadius:"8px", padding:"4px 10px", cursor:"pointer", fontWeight:600 }}>Nullstill</button>}
      </div>
      <div style={{ display:"flex", gap:"6px", overflowX:"auto", paddingBottom:"8px", marginBottom:"12px" }}>
        {INVENTORY_CATEGORIES.map((c,i) => (
          <button key={i} onClick={()=>setActiveCat(i)} style={{
            flexShrink:0, padding:"8px 14px", borderRadius:"10px", border:"none",
            background:activeCat===i?"var(--accent-green)":"var(--surface)", color:activeCat===i?"#0C0F0A":"var(--text-secondary)",
            fontSize:"12px", fontWeight:600, cursor:"pointer", whiteSpace:"nowrap",
          }}>
            {c.icon} {c.name}
          </button>
        ))}
      </div>
      <div style={{ display:"flex", flexDirection:"column", gap:"6px" }}>
        {cat.items.map((item,i) => (
          <div key={i} style={{
            display:"flex", alignItems:"center", justifyContent:"space-between",
            background:"var(--surface)", borderRadius:"10px", padding:"10px 14px", border:"1px solid var(--divider)",
          }}>
            <span style={{ fontSize:"14px", color:"var(--text-primary)", fontWeight:500 }}>{item}</span>
            <div style={{ display:"flex", alignItems:"center", gap:"8px" }}>
              <button onClick={()=>setCount(item, getCount(item)-1)} style={{ width:"32px", height:"32px", borderRadius:"8px", border:"1px solid var(--divider)", background:"var(--task-bg)", color:"var(--text-secondary)", fontSize:"18px", cursor:"pointer", display:"flex", alignItems:"center", justifyContent:"center" }}>−</button>
              <span style={{ fontSize:"15px", fontWeight:700, fontFamily:"monospace", color:"var(--accent-green)", minWidth:"28px", textAlign:"center" }}>{getCount(item)}</span>
              <button onClick={()=>setCount(item, getCount(item)+1)} style={{ width:"32px", height:"32px", borderRadius:"8px", border:"1px solid var(--divider)", background:"var(--task-bg)", color:"var(--text-secondary)", fontSize:"18px", cursor:"pointer", display:"flex", alignItems:"center", justifyContent:"center" }}>+</button>
            </div>
          </div>
        ))}
      </div>
    </div>
  );
}

function ReportPage() {
  const [report, setReport] = useState({ kasseStart: "2000", kasseSlutt: "", svinn: "", tgtg: "", kommentar: "", hendelser: "" });
  const diff = report.kasseSlutt ? (parseFloat(report.kasseSlutt) - parseFloat(report.kasseStart || 2000)) : null;
  const now = new Date();

  const Field = ({ label, field, placeholder, multi }) => (
    <div style={{ marginBottom:"10px" }}>
      <label style={{ fontSize:"12px", fontWeight:600, color:"var(--text-secondary)", marginBottom:"4px", display:"block", textTransform:"uppercase", letterSpacing:"0.05em" }}>{label}</label>
      {multi ? (
        <textarea value={report[field]} onChange={e=>setReport(p=>({...p,[field]:e.target.value}))} placeholder={placeholder}
          rows={3} style={{ width:"100%", background:"var(--task-bg)", border:"1px solid var(--divider)", borderRadius:"10px", padding:"10px 12px", color:"var(--text-primary)", fontSize:"14px", outline:"none", resize:"vertical", fontFamily:"inherit" }}/>
      ) : (
        <input value={report[field]} onChange={e=>setReport(p=>({...p,[field]:e.target.value}))} placeholder={placeholder}
          style={{ width:"100%", background:"var(--task-bg)", border:"1px solid var(--divider)", borderRadius:"10px", padding:"10px 12px", color:"var(--text-primary)", fontSize:"14px", outline:"none" }}/>
      )}
    </div>
  );

  return (
    <div>
      <div style={{ background:"var(--surface)", borderRadius:"14px", padding:"16px", border:"1px solid var(--divider)", marginBottom:"12px" }}>
        <div style={{ fontSize:"13px", fontWeight:700, color:"var(--text-secondary)", marginBottom:"12px", textTransform:"uppercase", letterSpacing:"0.05em" }}>
          📅 {now.toLocaleDateString("nb-NO", { weekday:"long", day:"numeric", month:"long", year:"numeric" })}
        </div>
        <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr", gap:"10px" }}>
          <Field label="Kasse start (kr)" field="kasseStart" placeholder="2000"/>
          <Field label="Kasse slutt (kr)" field="kasseSlutt" placeholder="Sum"/>
        </div>
        {diff !== null && (
          <div style={{ background: diff>=0?"rgba(74,222,111,0.1)":"rgba(238,39,55,0.08)", borderRadius:"10px", padding:"10px 14px", display:"flex", justifyContent:"space-between", alignItems:"center", marginTop:"4px" }}>
            <span style={{ fontSize:"13px", color:"var(--text-secondary)" }}>Differanse</span>
            <span style={{ fontSize:"16px", fontWeight:700, fontFamily:"monospace", color: diff>=0?"var(--accent-green)":"var(--accent-red)" }}>{diff>=0?"+":""}{diff.toFixed(0)} kr</span>
          </div>
        )}
      </div>
      <div style={{ background:"var(--surface)", borderRadius:"14px", padding:"16px", border:"1px solid var(--divider)", marginBottom:"12px" }}>
        <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr", gap:"10px", marginBottom:"4px" }}>
          <Field label="Svinn (kr)" field="svinn" placeholder="0"/>
          <Field label="TooGoodToGo (antall)" field="tgtg" placeholder="0"/>
        </div>
      </div>
      <div style={{ background:"var(--surface)", borderRadius:"14px", padding:"16px", border:"1px solid var(--divider)" }}>
        <Field label="Kommentar til neste vakt" field="kommentar" placeholder="F.eks. mangler melk, skap er tomt..." multi/>
        <Field label="Hendelser / Avvik" field="hendelser" placeholder="Noe spesielt som skjedde?" multi/>
      </div>
    </div>
  );
}

function TrainingPage() {
  const [activeModule, setActiveModule] = useState(null);
  const [completedSteps, setCompletedSteps] = useState({});

  if (activeModule !== null) {
    const mod = TRAINING_MODULES[activeModule];
    const done = mod.steps.filter((_,i)=>completedSteps[`${activeModule}-${i}`]).length;
    return (
      <div>
        <button onClick={()=>setActiveModule(null)} style={{ background:"none", border:"none", color:"var(--accent-green)", fontSize:"13px", fontWeight:600, cursor:"pointer", marginBottom:"14px", padding:0 }}>← Tilbake til moduler</button>
        <div style={{ background:"var(--surface)", borderRadius:"14px", padding:"16px", border:"1px solid var(--divider)", marginBottom:"14px" }}>
          <div style={{ fontSize:"28px", marginBottom:"6px" }}>{mod.icon}</div>
          <div style={{ fontSize:"18px", fontWeight:700, color:"var(--text-primary)", marginBottom:"2px" }}>{mod.title}</div>
          <div style={{ fontSize:"12px", color:"var(--accent-orange)", fontWeight:600 }}>{mod.difficulty}</div>
          <div style={{ fontSize:"12px", color:"var(--text-muted)", marginTop:"6px" }}>{done}/{mod.steps.length} steg fullført</div>
          <div style={{ height:"4px", background:"var(--ring-bg)", borderRadius:"2px", marginTop:"8px" }}>
            <div style={{ height:"100%", width:`${(done/mod.steps.length)*100}%`, background:"var(--accent-green)", borderRadius:"2px", transition:"width 0.3s" }}/>
          </div>
        </div>
        <div style={{ display:"flex", flexDirection:"column", gap:"6px" }}>
          {mod.steps.map((step,i)=>{
            const isDone = !!completedSteps[`${activeModule}-${i}`];
            return (
              <button key={i} onClick={()=>setCompletedSteps(p=>({...p,[`${activeModule}-${i}`]:!isDone}))} style={{
                display:"flex", alignItems:"flex-start", gap:"12px", width:"100%", padding:"12px 14px", border:"none",
                background: isDone?"var(--task-done-bg)":"var(--surface)", borderRadius:"10px", cursor:"pointer", textAlign:"left", borderLeft:"1px solid var(--divider)",
              }}>
                <div style={{ width:"24px", height:"24px", borderRadius:"50%", flexShrink:0, background: isDone?"var(--accent-green)":"var(--task-bg)", border: isDone?"none":"2px solid var(--check-border)", display:"flex", alignItems:"center", justifyContent:"center", fontSize:"12px", fontWeight:700, color: isDone?"#fff":"var(--text-muted)" }}>
                  {isDone ? "✓" : i+1}
                </div>
                <span style={{ fontSize:"14px", color: isDone?"var(--text-done)":"var(--text-primary)", fontWeight:500, lineHeight:1.4, textDecoration: isDone?"line-through":"none" }}>{step}</span>
              </button>
            );
          })}
        </div>
      </div>
    );
  }

  return (
    <div>
      <div style={{ fontSize:"13px", color:"var(--text-muted)", marginBottom:"14px" }}>Velg en modul for å starte opplæringen.</div>
      <div style={{ display:"flex", flexDirection:"column", gap:"8px" }}>
        {TRAINING_MODULES.map((mod,i)=>{
          const done = mod.steps.filter((_,si)=>completedSteps[`${i}-${si}`]).length;
          return (
            <button key={i} onClick={()=>setActiveModule(i)} style={{
              display:"flex", alignItems:"center", gap:"14px", width:"100%", padding:"16px",
              background:"var(--surface)", border:"1px solid var(--divider)", borderRadius:"14px", cursor:"pointer", textAlign:"left",
            }}>
              <div style={{ fontSize:"32px", flexShrink:0 }}>{mod.icon}</div>
              <div style={{ flex:1 }}>
                <div style={{ fontSize:"15px", fontWeight:700, color:"var(--text-primary)" }}>{mod.title}</div>
                <div style={{ fontSize:"11px", color:"var(--accent-orange)", fontWeight:600, marginTop:"2px" }}>{mod.difficulty} · {mod.steps.length} steg</div>
                {done>0 && <div style={{ height:"3px", background:"var(--ring-bg)", borderRadius:"2px", marginTop:"6px" }}>
                  <div style={{ height:"100%", width:`${(done/mod.steps.length)*100}%`, background:"var(--accent-green)", borderRadius:"2px" }}/>
                </div>}
              </div>
              <span style={{ color:"var(--text-muted)", fontSize:"18px" }}>▸</span>
            </button>
          );
        })}
      </div>
    </div>
  );
}

function ChatPage() {
  const [messages, setMessages] = useState([
    { from: "System", text: "Velkommen til 7-Eleven Hub chatten! Skriv meldinger til kollegaene dine.", time: "09:00", system: true },
  ]);
  const [input, setInput] = useState("");
  const [myName, setMyName] = useState("");
  const bottomRef = useRef(null);

  useEffect(() => { bottomRef.current?.scrollIntoView({ behavior: "smooth" }); }, [messages]);

  const send = () => {
    if (!input.trim() || !myName.trim()) return;
    const now = new Date();
    setMessages(p => [...p, { from: myName, text: input, time: now.getHours().toString().padStart(2,"0")+":"+now.getMinutes().toString().padStart(2,"0") }]);
    setInput("");
  };

  return (
    <div style={{ display:"flex", flexDirection:"column", height:"calc(100vh - 200px)" }}>
      {!myName.trim() ? (
        <div style={{ background:"var(--surface)", borderRadius:"14px", padding:"20px", border:"1px solid var(--divider)" }}>
          <div style={{ fontSize:"14px", fontWeight:600, color:"var(--text-primary)", marginBottom:"10px" }}>Skriv inn navnet ditt for å starte</div>
          <div style={{ display:"flex", gap:"8px" }}>
            <input value={myName} onChange={e=>setMyName(e.target.value)} placeholder="Ditt navn..." onKeyDown={e=>e.key==="Enter"&&myName.trim()&&setMyName(myName.trim())}
              style={{ flex:1, background:"var(--task-bg)", border:"1px solid var(--divider)", borderRadius:"10px", padding:"10px 12px", color:"var(--text-primary)", fontSize:"14px", outline:"none" }}/>
            <button onClick={()=>myName.trim()&&setMyName(myName.trim())} style={{ background:"var(--accent-green)", border:"none", borderRadius:"10px", padding:"10px 16px", color:"#0C0F0A", fontWeight:700, cursor:"pointer" }}>Start</button>
          </div>
        </div>
      ) : (
        <>
          <div style={{ flex:1, overflowY:"auto", display:"flex", flexDirection:"column", gap:"8px", paddingBottom:"10px" }}>
            {messages.map((m,i) => (
              <div key={i} style={{
                alignSelf: m.system?"center":m.from===myName?"flex-end":"flex-start",
                maxWidth: m.system?"90%":"80%",
                background: m.system?"var(--ring-bg)":m.from===myName?"var(--accent-green)":"var(--surface)",
                color: m.system?"var(--text-muted)":m.from===myName?"#0C0F0A":"var(--text-primary)",
                borderRadius:"12px", padding:"10px 14px", fontSize: m.system?"12px":"14px",
                border: m.system?"none":"1px solid var(--divider)",
              }}>
                {!m.system && <div style={{ fontSize:"11px", fontWeight:700, marginBottom:"3px", opacity:0.7 }}>{m.from} · {m.time}</div>}
                <div>{m.text}</div>
              </div>
            ))}
            <div ref={bottomRef}/>
          </div>
          <div style={{ display:"flex", gap:"8px", paddingTop:"10px", borderTop:"1px solid var(--divider)" }}>
            <input value={input} onChange={e=>setInput(e.target.value)} placeholder="Skriv en melding..."
              onKeyDown={e=>e.key==="Enter"&&send()}
              style={{ flex:1, background:"var(--task-bg)", border:"1px solid var(--divider)", borderRadius:"10px", padding:"10px 12px", color:"var(--text-primary)", fontSize:"14px", outline:"none" }}/>
            <button onClick={send} style={{ background:"var(--accent-green)", border:"none", borderRadius:"10px", padding:"10px 16px", color:"#0C0F0A", fontWeight:700, cursor:"pointer" }}>Send</button>
          </div>
        </>
      )}
    </div>
  );
}

// ─── MAIN APP ────────────────────────────────────────────────────────
const SUPPLIER_URLS = {
  "oppe": "https://beta.engrospartner.no",
  "nede": "https://beta.engrospartner.no",
  "kolly": "https://beta.engrospartner.no",
  "ringnes": "https://www.ringnesbestilling.no",
  "tine": "https://www.tinehandel.no",
  "diplom": "https://beta.engrospartner.no",
  "bama": "https://www.bama.no",
};

const WEEKLY_NEEDS = {
  "24704":10,"73528":10,"73316":1,"67596":2,"25667":1,"29134":6,"71902":2,"68241":6,
  "74767":12,"74800":3,"74798":3,"23863":3,"72720":9,"72722":2,"63289":10,"71274":2,
  "64826":2,"69221":2,"68837":1,"28819":1,"22428":1,
  "24512":2,"24510":1,"24511":1,"74196":1,"24713":1,
  "66608":2,"72576":3,"19239":2,"22463":2,"22464":2,"60367":2,
  "71774":3,"73447":3,"71831":4,"19222":6,"72689":1,"68606":6,"68607":6,"72599":2,"74058":19,
  "71856":1,"69532":1,"61655":1,
};

// ─── GOOGLE SHEETS PARSER ────────────────────────────────────────────
const SHEET_NAMES = ["OPPE Bestilling","NEDE Bestilling","Kolly Drikke","Diplom IS","Ringnes","TINE Handel","Bama Storkjøkken"];
const SHEET_ICONS = {"OPPE Bestilling":"🏪","NEDE Bestilling":"⬇️","Kolly Drikke":"🥤","Diplom IS":"🍦","Ringnes":"🍋","TINE Handel":"🥛","Bama Storkjøkken":"🥬"};

function parseCSV(text) {
  const lines = []; let cur = ""; let inQ = false;
  for (let i = 0; i < text.length; i++) {
    const c = text[i];
    if (c === '"') { inQ = !inQ; cur += c; }
    else if (c === '\n' && !inQ) { lines.push(cur); cur = ""; }
    else { cur += c; }
  }
  if (cur) lines.push(cur);
  return lines.map(line => {
    const cells = []; let cell = ""; let q = false;
    for (let i = 0; i < line.length; i++) {
      const c = line[i];
      if (c === '"') { q = !q; } else if (c === ',' && !q) { cells.push(cell.trim()); cell = ""; } else { cell += c; }
    }
    cells.push(cell.trim());
    return cells;
  });
}

function parseSheetToSupplier(rows, sheetName) {
  const isTine = sheetName === "TINE Handel";
  const isBama = sheetName === "Bama Storkjøkken";
  const colOffset = (isTine || isBama) ? 0 : 1;
  const sections = []; let currentSection = null;

  for (let r = 4; r < rows.length; r++) {
    const row = rows[r];
    if (!row || row.length < 4) continue;

    const nameCol = isTine ? 1 : isBama ? 0 : 3;
    const varenrCol = isTine ? 0 : isBama ? -1 : 1;
    const fpakCol = isTine ? 3 : isBama ? 2 : 5;
    const prisFpakCol = isTine ? 5 : isBama ? 3 : 7;
    const cellName = (row[nameCol] || "").toString().trim();
    const cellNr = varenrCol >= 0 ? (row[varenrCol] || "").toString().trim() : "";

    if (!cellName || cellName === "TOTALT" || cellName === "TOTALER") continue;

    const isSection = cellName.match(/^[\u{1F300}-\u{1FAFF}\u{2600}-\u{26FF}]/u) && (!cellNr || cellNr === "" || cellNr === "🔗");
    const isDataRow = !isSection && cellName.length > 3 && cellName !== "Varenavn" && cellName !== "NaN";

    if (isSection) {
      currentSection = { name: cellName, items: [] };
      sections.push(currentSection);
    } else if (isDataRow && currentSection) {
      const fpak = parseFloat(row[fpakCol]) || 1;
      const pris = parseFloat(row[prisFpakCol]) || 0;
      currentSection.items.push({ name: cellName, nr: cellNr, dpak: 1, fpak, pris });
    } else if (isDataRow && !currentSection) {
      currentSection = { name: "📦 Varer", items: [] };
      sections.push(currentSection);
      const fpak = parseFloat(row[fpakCol]) || 1;
      const pris = parseFloat(row[prisFpakCol]) || 0;
      currentSection.items.push({ name: cellName, nr: cellNr, dpak: 1, fpak, pris });
    }
  }
  return {
    id: sheetName.replace(/\s+/g, "_").toLowerCase(),
    name: sheetName.replace(" Bestilling", ""),
    icon: SHEET_ICONS[sheetName] || "📦",
    sections: sections.filter(s => s.items.length > 0),
  };
}

function OrdrePage() {
  const [activeSupplier, setActiveSupplier] = useState(0);
  const [activeSection, setActiveSection] = useState(0);
  const [stock, setStock] = useState({});
  const [needs, setNeeds] = useState({...WEEKLY_NEEDS});
  const [orderDay, setOrderDay] = useState("MAN");
  const [mode, setMode] = useState("tell"); // "tell" | "bestill"
  const [sheetId, setSheetId] = useState("");
  const [sheetInput, setSheetInput] = useState("");
  const [liveData, setLiveData] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);

  const suppliers = liveData || ORDRE_SUPPLIERS;
  const supplier = suppliers[activeSupplier] || suppliers[0];
  const section = supplier.sections[activeSection] || supplier.sections[0];

  const fetchSheets = async (id) => {
    setLoading(true); setError(null);
    try {
      const results = [];
      for (const name of SHEET_NAMES) {
        const url = `https://docs.google.com/spreadsheets/d/${id}/gviz/tq?tqx=out:csv&sheet=${encodeURIComponent(name)}`;
        const res = await fetch(url);
        if (!res.ok) continue;
        const text = await res.text();
        const rows = parseCSV(text);
        const parsed = parseSheetToSupplier(rows, name);
        if (parsed.sections.length > 0) results.push(parsed);
      }
      if (results.length === 0) throw new Error("Ingen data funnet");
      setLiveData(results); setSheetId(id);
      setActiveSupplier(0); setActiveSection(0);
    } catch (e) { setError(e.message); }
    setLoading(false);
  };
  const extractId = (input) => { const m = input.match(/\/d\/([a-zA-Z0-9_-]+)/); return m ? m[1] : input.trim(); };

  const getStock = (key) => stock[key] || 0;
  const setStockVal = (key, val) => setStock(p => ({...p, [key]: Math.max(0, val)}));
  const getNeed = (nr) => needs[nr] || 0;
  const setNeedVal = (nr, val) => setNeeds(p => ({...p, [nr]: Math.max(0, val)}));

  const calcOrder = (item) => {
    const key = item.nr || item.name;
    const currentStock = getStock(key);
    const weeklyNeed = getNeed(key);
    const deficit = weeklyNeed - currentStock;
    if (deficit <= 0) return 0;
    return Math.ceil(deficit / (item.fpak || 1));
  };

  // Compute totals for bestillingsliste
  const allOrders = [];
  suppliers.forEach(sup => {
    sup.sections.forEach(sec => {
      sec.items.forEach(item => {
        const qty = calcOrder(item);
        if (qty > 0) allOrders.push({ ...item, qty, supplier: sup.name, supplierId: sup.id, supplierIcon: sup.icon });
      });
    });
  });
  const ordersBySup = {};
  allOrders.forEach(o => {
    if (!ordersBySup[o.supplierId]) ordersBySup[o.supplierId] = { name: o.supplier, icon: o.supplierIcon, url: SUPPLIER_URLS[o.supplierId] || "", items: [] };
    ordersBySup[o.supplierId].items.push(o);
  });

  const totalCounted = Object.keys(stock).length;
  const totalToOrder = allOrders.length;

  return (
    <div>
      {/* Google Sheets Connection */}
      <div style={{ background: sheetId ? "rgba(74,222,111,0.08)" : "var(--surface)", borderRadius:"12px", padding:"10px 14px", border: sheetId ? "1px solid rgba(0,135,81,0.15)" : "1px solid var(--divider)", marginBottom:"10px" }}>
        {sheetId ? (
          <div style={{ display:"flex", alignItems:"center", justifyContent:"space-between" }}>
            <div style={{ display:"flex", alignItems:"center", gap:"6px" }}>
              <div style={{ width:"7px", height:"7px", borderRadius:"50%", background:"var(--accent-green)", animation:"pulse 2s infinite" }}/>
              <span style={{ fontSize:"11px", color:"var(--accent-green)", fontWeight:600 }}>Live fra Google Sheets</span>
            </div>
            <div style={{ display:"flex", gap:"4px" }}>
              <button onClick={()=>fetchSheets(sheetId)} style={{ fontSize:"10px", color:"var(--accent-orange)", background:"rgba(245,158,11,0.1)", border:"1px solid rgba(245,158,11,0.2)", borderRadius:"6px", padding:"3px 7px", cursor:"pointer", fontWeight:600 }}>↻</button>
              <button onClick={()=>{setSheetId("");setLiveData(null);}} style={{ fontSize:"10px", color:"var(--accent-red)", background:"rgba(238,39,55,0.08)", border:"1px solid rgba(239,68,68,0.2)", borderRadius:"6px", padding:"3px 7px", cursor:"pointer", fontWeight:600 }}>✕</button>
            </div>
          </div>
        ) : (
          <div>
            <div style={{ fontSize:"11px", fontWeight:600, color:"var(--text-secondary)", marginBottom:"6px" }}>📊 Koble til Google Sheets (valgfritt)</div>
            <div style={{ display:"flex", gap:"5px" }}>
              <input value={sheetInput} onChange={e=>setSheetInput(e.target.value)} placeholder="Google Sheets URL eller ID..."
                onKeyDown={e=>e.key==="Enter" && sheetInput.trim() && fetchSheets(extractId(sheetInput))}
                style={{ flex:1, background:"var(--task-bg)", border:"1px solid var(--divider)", borderRadius:"8px", padding:"7px 9px", color:"var(--text-primary)", fontSize:"11px", outline:"none" }}/>
              <button onClick={()=>sheetInput.trim() && fetchSheets(extractId(sheetInput))} disabled={loading}
                style={{ background:"var(--accent-green)", border:"none", borderRadius:"8px", padding:"7px 12px", color:"#0C0F0A", fontWeight:700, cursor:"pointer", fontSize:"11px" }}>
                {loading ? "..." : "Koble"}
              </button>
            </div>
            {error && <div style={{ fontSize:"10px", color:"var(--accent-red)", marginTop:"4px" }}>⚠️ {error}</div>}
          </div>
        )}
      </div>

      {/* Mode Toggle: Tell lager vs Bestillingsliste */}
      <div style={{ display:"flex", gap:"4px", background:"var(--surface)", borderRadius:"12px", padding:"3px", border:"1px solid var(--divider)", marginBottom:"12px" }}>
        <button onClick={()=>setMode("tell")} style={{
          flex:1, padding:"10px", borderRadius:"10px", border:"none", cursor:"pointer", fontSize:"13px", fontWeight:700,
          background: mode==="tell"?"var(--accent-green)":"transparent", color: mode==="tell"?"#0C0F0A":"var(--text-muted)",
        }}>📦 Tell lager</button>
        <button onClick={()=>setMode("bestill")} style={{
          flex:1, padding:"10px", borderRadius:"10px", border:"none", cursor:"pointer", fontSize:"13px", fontWeight:700, position:"relative",
          background: mode==="bestill"?"var(--accent-orange)":"transparent", color: mode==="bestill"?"#0C0F0A":"var(--text-muted)",
        }}>
          📋 Bestillingsliste
          {totalToOrder > 0 && <span style={{ position:"absolute", top:"-4px", right:"8px", background:"var(--accent-red)", color:"#fff", fontSize:"10px", fontWeight:700, borderRadius:"10px", padding:"1px 6px", minWidth:"18px", textAlign:"center" }}>{totalToOrder}</span>}
        </button>
      </div>

      {mode === "tell" ? (
        <>
          {/* Stats */}
          <div style={{ display:"flex", gap:"8px", marginBottom:"12px" }}>
            <div style={{ flex:1, background:"var(--surface)", borderRadius:"10px", padding:"10px 12px", border:"1px solid var(--divider)", textAlign:"center" }}>
              <div style={{ fontSize:"20px", fontWeight:700, color:"var(--accent-green)", fontFamily:"monospace" }}>{totalCounted}</div>
              <div style={{ fontSize:"10px", color:"var(--text-muted)" }}>Varer telt</div>
            </div>
            <div style={{ flex:1, background:"var(--surface)", borderRadius:"10px", padding:"10px 12px", border:"1px solid var(--divider)", textAlign:"center" }}>
              <div style={{ fontSize:"20px", fontWeight:700, color: totalToOrder>0?"var(--accent-red)":"var(--accent-green)", fontFamily:"monospace" }}>{totalToOrder}</div>
              <div style={{ fontSize:"10px", color:"var(--text-muted)" }}>Må bestilles</div>
            </div>
          </div>

          {/* Supplier tabs */}
          <div style={{ display:"flex", gap:"5px", overflowX:"auto", paddingBottom:"6px", marginBottom:"8px" }}>
            {suppliers.map((s,i) => (
              <button key={s.id} onClick={()=>{setActiveSupplier(i);setActiveSection(0);}} style={{
                flexShrink:0, padding:"7px 11px", borderRadius:"10px", border:"none",
                background: activeSupplier===i?"var(--accent-green)":"var(--surface)", color: activeSupplier===i?"#0C0F0A":"var(--text-secondary)",
                fontSize:"11px", fontWeight:600, cursor:"pointer", whiteSpace:"nowrap",
              }}>{s.icon} {s.name}</button>
            ))}
          </div>

          {/* Section tabs */}
          {supplier.sections.length > 1 && (
            <div style={{ display:"flex", gap:"4px", overflowX:"auto", paddingBottom:"6px", marginBottom:"8px" }}>
              {supplier.sections.map((sec,i) => (
                <button key={i} onClick={()=>setActiveSection(i)} style={{
                  flexShrink:0, padding:"5px 9px", borderRadius:"8px",
                  border: activeSection===i?"1px solid var(--accent-orange)":"1px solid var(--divider)",
                  background:"var(--surface)", color: activeSection===i?"var(--accent-orange)":"var(--text-muted)",
                  fontSize:"10.5px", fontWeight:600, cursor:"pointer", whiteSpace:"nowrap",
                }}>{sec.name}</button>
              ))}
            </div>
          )}

          {/* Items - count mode */}
          <div style={{ display:"flex", flexDirection:"column", gap:"5px" }}>
            {section && section.items.map((item,i) => {
              const key = item.nr || item.name;
              const counted = getStock(key);
              const need = getNeed(key);
              const orderQty = calcOrder(item);
              return (
                <div key={i} style={{
                  background: orderQty > 0 ? "rgba(239,68,68,0.04)" : counted > 0 ? "rgba(74,222,111,0.04)" : "var(--surface)",
                  borderRadius:"10px", padding:"10px 12px",
                  border: orderQty > 0 ? "1px solid rgba(239,68,68,0.15)" : counted > 0 ? "1px solid var(--divider)" : "1px solid var(--divider)",
                }}>
                  <div style={{ marginBottom:"8px" }}>
                    <div style={{ fontSize:"13px", color:"var(--text-primary)", fontWeight:500, lineHeight:1.3 }}>{item.name}</div>
                    <div style={{ display:"flex", gap:"8px", marginTop:"2px", flexWrap:"wrap" }}>
                      {item.nr && <span style={{ fontSize:"10px", color:"var(--text-muted)", fontFamily:"monospace" }}>#{item.nr}</span>}
                      <span style={{ fontSize:"10px", color:"var(--text-muted)" }}>{item.fpak} stk/pak</span>
                    </div>
                  </div>
                  <div style={{ display:"flex", gap:"8px" }}>
                    {/* Lager */}
                    <div style={{ flex:1, background:"var(--task-bg)", borderRadius:"8px", padding:"8px" }}>
                      <div style={{ fontSize:"9px", color:"var(--text-muted)", fontWeight:600, textTransform:"uppercase", marginBottom:"4px" }}>På lager (stk)</div>
                      <div style={{ display:"flex", alignItems:"center", gap:"6px", justifyContent:"center" }}>
                        <button onClick={()=>setStockVal(key, counted-1)} style={{ width:"26px", height:"26px", borderRadius:"6px", border:"1px solid var(--divider)", background:"var(--surface)", color:"var(--text-secondary)", fontSize:"14px", cursor:"pointer", display:"flex", alignItems:"center", justifyContent:"center" }}>−</button>
                        <span style={{ fontSize:"16px", fontWeight:700, fontFamily:"monospace", color:"var(--text-primary)", minWidth:"24px", textAlign:"center" }}>{counted}</span>
                        <button onClick={()=>setStockVal(key, counted+1)} style={{ width:"26px", height:"26px", borderRadius:"6px", border:"1px solid var(--divider)", background:"var(--surface)", color:"var(--text-secondary)", fontSize:"14px", cursor:"pointer", display:"flex", alignItems:"center", justifyContent:"center" }}>+</button>
                      </div>
                    </div>
                    {/* Ukebehov */}
                    <div style={{ flex:1, background:"var(--task-bg)", borderRadius:"8px", padding:"8px" }}>
                      <div style={{ fontSize:"9px", color:"var(--accent-orange)", fontWeight:600, textTransform:"uppercase", marginBottom:"4px" }}>Ukebehov</div>
                      <div style={{ display:"flex", alignItems:"center", gap:"6px", justifyContent:"center" }}>
                        <button onClick={()=>setNeedVal(key, need-1)} style={{ width:"26px", height:"26px", borderRadius:"6px", border:"1px solid var(--divider)", background:"var(--surface)", color:"var(--text-secondary)", fontSize:"14px", cursor:"pointer", display:"flex", alignItems:"center", justifyContent:"center" }}>−</button>
                        <span style={{ fontSize:"16px", fontWeight:700, fontFamily:"monospace", color:"var(--accent-orange)", minWidth:"24px", textAlign:"center" }}>{need}</span>
                        <button onClick={()=>setNeedVal(key, need+1)} style={{ width:"26px", height:"26px", borderRadius:"6px", border:"1px solid var(--divider)", background:"var(--surface)", color:"var(--text-secondary)", fontSize:"14px", cursor:"pointer", display:"flex", alignItems:"center", justifyContent:"center" }}>+</button>
                      </div>
                    </div>
                    {/* Result */}
                    <div style={{ width:"60px", background: orderQty>0?"rgba(238,39,55,0.08)":"rgba(74,222,111,0.1)", borderRadius:"8px", padding:"8px", display:"flex", flexDirection:"column", alignItems:"center", justifyContent:"center" }}>
                      <div style={{ fontSize:"9px", color: orderQty>0?"var(--accent-red)":"var(--accent-green)", fontWeight:600, marginBottom:"2px" }}>BESTILL</div>
                      <div style={{ fontSize:"18px", fontWeight:800, fontFamily:"monospace", color: orderQty>0?"var(--accent-red)":"var(--accent-green)" }}>{orderQty}</div>
                      <div style={{ fontSize:"8px", color:"var(--text-muted)" }}>D-pak</div>
                    </div>
                  </div>
                </div>
              );
            })}
          </div>
        </>
      ) : (
        /* ── BESTILLINGSLISTE MODE ── */
        <div>
          {totalToOrder === 0 ? (
            <div style={{ textAlign:"center", padding:"40px 20px" }}>
              <div style={{ fontSize:"40px", marginBottom:"12px" }}>✅</div>
              <div style={{ fontSize:"16px", fontWeight:700, color:"var(--text-primary)", marginBottom:"6px" }}>Ingenting å bestille!</div>
              <div style={{ fontSize:"13px", color:"var(--text-muted)" }}>Alle varer er på lager, eller du har ikke talt ennå. Gå til «Tell lager» for å starte.</div>
            </div>
          ) : (
            <div style={{ display:"flex", flexDirection:"column", gap:"12px" }}>
              {Object.values(ordersBySup).map((sup, si) => (
                <div key={si} style={{ background:"var(--surface)", borderRadius:"14px", border:"1px solid var(--divider)", overflow:"hidden" }}>
                  <div style={{ padding:"12px 14px", borderBottom:"1px solid var(--divider)", display:"flex", alignItems:"center", justifyContent:"space-between" }}>
                    <div>
                      <div style={{ fontSize:"14px", fontWeight:700, color:"var(--text-primary)" }}>{sup.icon} {sup.name}</div>
                      <div style={{ fontSize:"11px", color:"var(--text-muted)" }}>{sup.items.length} varer å bestille</div>
                    </div>
                    {sup.url && (
                      <a href={sup.url} target="_blank" rel="noopener noreferrer" style={{
                        fontSize:"11px", fontWeight:700, color:"#0C0F0A", background:"var(--accent-green)", borderRadius:"8px",
                        padding:"6px 12px", textDecoration:"none", display:"flex", alignItems:"center", gap:"4px",
                      }}>🌐 Bestill</a>
                    )}
                  </div>
                  <div style={{ padding:"8px" }}>
                    {sup.items.map((item, ii) => (
                      <div key={ii} style={{
                        display:"flex", alignItems:"center", justifyContent:"space-between",
                        padding:"8px 10px", borderRadius:"8px",
                        background: ii % 2 === 0 ? "transparent" : "var(--task-bg)",
                      }}>
                        <div style={{ flex:1 }}>
                          <div style={{ fontSize:"13px", color:"var(--text-primary)", fontWeight:500 }}>{item.name}</div>
                          <div style={{ fontSize:"10px", color:"var(--text-muted)", fontFamily:"monospace" }}>
                            {item.nr && `#${item.nr} · `}{item.fpak} stk/pak
                          </div>
                        </div>
                        <div style={{ textAlign:"right" }}>
                          <div style={{ fontSize:"18px", fontWeight:800, color:"var(--accent-red)", fontFamily:"monospace" }}>{item.qty}</div>
                          <div style={{ fontSize:"9px", color:"var(--text-muted)" }}>D-pak</div>
                        </div>
                      </div>
                    ))}
                  </div>
                </div>
              ))}

              {/* Copy summary */}
              <button onClick={() => {
                const text = Object.values(ordersBySup).map(s =>
                  `${s.name}:\n` + s.items.map(i => `  ${i.qty}x D-pak - ${i.name}${i.nr ? ` (#${i.nr})` : ""}`).join("\n")
                ).join("\n\n");
                navigator.clipboard?.writeText(text);
              }} style={{
                width:"100%", padding:"12px", borderRadius:"12px", border:"1px dashed var(--divider)",
                background:"var(--surface)", color:"var(--text-secondary)", fontSize:"13px", fontWeight:600, cursor:"pointer",
              }}>
                📋 Kopier bestillingsliste
              </button>
            </div>
          )}
        </div>
      )}

      {/* Reset */}
      {totalCounted > 0 && (
        <button onClick={()=>{setStock({});}} style={{
          width:"100%", marginTop:"14px", padding:"10px", borderRadius:"10px",
          border:"1px solid rgba(239,68,68,0.2)", background:"rgba(239,68,68,0.05)",
          color:"var(--accent-red)", fontSize:"12px", fontWeight:600, cursor:"pointer",
        }}>🗑 Nullstill lagertelling</button>
      )}
    </div>
  );
}

function HomePage({ setPage, checked, user, logout }) {
  const now = new Date();
  const hour = now.getHours();
  const greeting = hour < 10 ? "God morgen" : hour < 17 ? "Hei" : "God kveld";
  const firstName = user?.name?.split(" ")[0] || "";
  const dayName = now.toLocaleDateString("nb-NO", { weekday: "long" });
  const dateStr = now.toLocaleDateString("nb-NO", { day: "numeric", month: "long", year: "numeric" });

  // Calculate checklist progress
  const totalAll = Object.values(CHECKLISTS).reduce((a, l) => a + l.sections.reduce((b, s) => b + s.tasks.length, 0), 0);
  const doneAll = Object.entries(CHECKLISTS).reduce((a, [k, l]) => a + l.sections.reduce((b, s) => b + s.tasks.filter(t => checked[k]?.[t.id]).length, 0), 0);
  const pctAll = totalAll ? Math.round((doneAll / totalAll) * 100) : 0;

  // Time-based shift info
  const currentShift = hour < 10 ? "Åpningsvakt" : hour < 15 ? "Dagvakt" : "Kveldsvakt";

  const QuickLink = ({ icon, label, sublabel, color, onClick }) => (
    <button onClick={onClick} style={{
      background: "var(--surface)", border: "1px solid var(--divider)", borderRadius: "14px",
      padding: "14px", cursor: "pointer", textAlign: "left", width: "100%",
      display: "flex", alignItems: "center", gap: "12px", transition: "all 0.2s",
    }}>
      <div style={{ width: "42px", height: "42px", borderRadius: "12px", background: `${color}15`, border: `1px solid ${color}30`,
        display: "flex", alignItems: "center", justifyContent: "center", fontSize: "20px", flexShrink: 0 }}>{icon}</div>
      <div style={{ flex: 1 }}>
        <div style={{ fontSize: "14px", fontWeight: 700, color: "var(--text-primary)" }}>{label}</div>
        <div style={{ fontSize: "11px", color: "var(--text-muted)", marginTop: "1px" }}>{sublabel}</div>
      </div>
      <span style={{ color: "var(--text-muted)", fontSize: "16px" }}>›</span>
    </button>
  );

  return (
    <div>
      {/* Green header with logo */}
      <div style={{ background: "linear-gradient(135deg, #008751, #00A86B)", margin: "-16px -16px 16px", padding: "20px 20px 24px", borderRadius: "0 0 28px 28px", position: "relative", overflow: "hidden" }}>
        <div style={{ position: "absolute", top: "-20px", right: "-10px", width: "100px", height: "100px", borderRadius: "50%", background: "rgba(255,255,255,0.08)" }}/>
        <div style={{ position: "absolute", bottom: "-30px", left: "20px", width: "80px", height: "80px", borderRadius: "50%", background: "rgba(255,255,255,0.05)" }}/>
        <div style={{ display: "flex", alignItems: "center", justifyContent: "space-between", position: "relative" }}>
          <img src={LOGO} alt="7-Eleven" style={{ width: "56px", height: "auto", filter: "drop-shadow(0 2px 6px rgba(0,0,0,0.15))" }}/>
          <button onClick={logout} style={{ display: "flex", alignItems: "center", gap: "8px", background: "rgba(255,255,255,0.2)", border: "none", borderRadius: "12px", padding: "6px 12px", cursor: "pointer" }}>
            <div style={{ width: "28px", height: "28px", borderRadius: "8px", background: "rgba(255,255,255,0.3)", display: "flex", alignItems: "center", justifyContent: "center", fontSize: "10px", fontWeight: 900, color: "#fff" }}>{user?.avatar}</div>
            <span style={{ fontSize: "12px", fontWeight: 700, color: "#fff" }}>{firstName}</span>
          </button>
        </div>
        <div style={{ marginTop: "14px", position: "relative" }}>
          <h1 style={{ fontSize: "24px", fontWeight: 900, color: "#fff" }}>{greeting}, {firstName}!</h1>
          <p style={{ fontSize: "13px", color: "rgba(255,255,255,0.75)", marginTop: "2px", textTransform: "capitalize" }}>{dayName} {dateStr}</p>
        </div>
      </div>

      {/* Current Status Cards */}
      <div style={{ display: "flex", gap: "8px", marginBottom: "14px" }}>
        <div style={{ flex: 1, background: "#FFFFFF", borderRadius: "14px", padding: "14px", border: "1px solid var(--divider)" }}>
          <div style={{ fontSize: "10px", color: "var(--accent-green)", fontWeight: 700, letterSpacing: "0.05em", marginBottom: "6px" }}>VAKT NÅ</div>
          <div style={{ fontSize: "17px", fontWeight: 800, color: "var(--text-primary)" }}>{currentShift}</div>
          <div style={{ fontSize: "11px", color: "var(--text-muted)", marginTop: "2px" }}>{now.toLocaleTimeString("nb-NO", { hour: "2-digit", minute: "2-digit" })}</div>
        </div>
        <div style={{ flex: 1, background: "#FFFFFF", borderRadius: "14px", padding: "14px", border: "1px solid var(--divider)" }}>
          <div style={{ fontSize: "10px", color: "var(--accent-orange)", fontWeight: 700, letterSpacing: "0.05em", marginBottom: "6px" }}>SJEKKLISTE</div>
          <div style={{ fontSize: "17px", fontWeight: 800, color: "var(--text-primary)" }}>{pctAll}% ferdig</div>
          <div style={{ fontSize: "11px", color: "var(--text-muted)", marginTop: "2px" }}>{doneAll} av {totalAll} oppgaver</div>
        </div>
      </div>

      {/* Today's Team */}
      <div style={{ background: "var(--surface)", borderRadius: "14px", padding: "14px", border: "1px solid var(--divider)", marginBottom: "14px" }}>
        <div style={{ fontSize: "11px", fontWeight: 700, color: "var(--text-secondary)", letterSpacing: "0.05em", marginBottom: "10px" }}>👥 PÅ JOBB I DAG</div>
        <div style={{ display: "flex", gap: "8px", flexWrap: "wrap" }}>
          {[
            { name: "Jatharthan M.", shift: "15:15–23:00", color: "#2563eb" },
            { name: "Yousef A.", shift: "07:00–15:00", color: "#0d9488" },
            { name: "Christine J.", shift: "17:00–00:00", color: "#16a34a" },
            { name: "Mansoor R.", shift: "12:00–19:00", color: "#7c3aed" },
          ].map((person, i) => (
            <div key={i} style={{ display: "flex", alignItems: "center", gap: "8px", background: "var(--task-bg)", borderRadius: "10px", padding: "8px 10px", flex: "1 1 45%", borderLeft: `3px solid ${person.color}` }}>
              <div>
                <div style={{ fontSize: "12px", fontWeight: 600, color: "var(--text-primary)" }}>{person.name}</div>
                <div style={{ fontSize: "10px", color: "var(--text-muted)", fontFamily: "monospace" }}>{person.shift}</div>
              </div>
            </div>
          ))}
        </div>
      </div>

      {/* Daily Reminders */}
      <div style={{ background: "#FFF8F0", borderRadius: "14px", padding: "14px", border: "1px solid rgba(245,158,11,0.2)", marginBottom: "14px" }}>
        <div style={{ fontSize: "11px", fontWeight: 700, color: "var(--accent-orange)", letterSpacing: "0.05em", marginBottom: "8px" }}>⚡ DAGENS PÅMINNELSER</div>
        <div style={{ display: "flex", flexDirection: "column", gap: "6px" }}>
          {[
            "Sjekk dato på yoghurt, smoothie og wraps",
            "Bestillingsfrist Engrospartner: mandag og onsdag",
            "Husk temperaturkontroll pølser og kjølevarer",
            "Too Good To Go — pakk og legg ut innen kl. 14",
          ].map((reminder, i) => (
            <div key={i} style={{ display: "flex", alignItems: "flex-start", gap: "8px" }}>
              <span style={{ color: "var(--accent-orange)", fontSize: "10px", marginTop: "3px" }}>●</span>
              <span style={{ fontSize: "12.5px", color: "var(--text-secondary)", lineHeight: 1.4 }}>{reminder}</span>
            </div>
          ))}
        </div>
      </div>

      {/* Quick Links */}
      <div style={{ fontSize: "11px", fontWeight: 700, color: "var(--text-secondary)", letterSpacing: "0.05em", marginBottom: "8px" }}>HURTIGMENY</div>
      <div style={{ display: "flex", flexDirection: "column", gap: "6px" }}>
        <QuickLink icon="📋" label="Sjekklister" sublabel={`${doneAll}/${totalAll} oppgaver fullført`} color="#4ADE6F" onClick={() => setPage("sjekk")} />
        <QuickLink icon="📦" label="Bestilling & Lager" sublabel="Tell lager og generer bestilling" color="#F59E0B" onClick={() => setPage("ordre")} />
        <QuickLink icon="⏱" label="Tid & Vakter" sublabel="Stempling, timeliste og vaktplan" color="#3B82F6" onClick={() => setPage("vakt")} />
        <QuickLink icon="📄" label="Dagsrapport" sublabel="Kasseoppgjør, svinn og kommentarer" color="#8B5CF6" onClick={() => setPage("rapport")} />
        <QuickLink icon="📖" label="Opplæring" sublabel="Rutiner og prosedyrer" color="#EC4899" onClick={() => setPage("laering")} />
        <QuickLink icon="💬" label="Chat" sublabel="Meldinger til kollegaer" color="#06B6D4" onClick={() => setPage("chat")} />
      </div>

      {/* Tidsbanken link */}
      <a href="https://min.tidsbanken.net/hjem?key=e1b88004-8551-47bc-9e38-fc050fb2c964" target="_blank" rel="noopener noreferrer" style={{
        display: "flex", alignItems: "center", justifyContent: "space-between", padding: "12px 14px",
        background: "var(--surface)", borderRadius: "14px", border: "1px solid var(--divider)",
        textDecoration: "none", marginTop: "12px",
      }}>
        <div style={{ display: "flex", alignItems: "center", gap: "10px" }}>
          <div style={{ width: "42px", height: "42px", borderRadius: "12px", background: "rgba(74,222,111,0.1)", border: "1px solid rgba(0,135,81,0.15)", display: "flex", alignItems: "center", justifyContent: "center", fontSize: "20px" }}>⏱</div>
          <div>
            <div style={{ fontSize: "14px", fontWeight: 700, color: "var(--text-primary)" }}>Tidsbanken</div>
            <div style={{ fontSize: "11px", color: "var(--text-muted)" }}>Offisiell stempling og timeliste</div>
          </div>
        </div>
        <span style={{ fontSize: "12px", color: "var(--accent-green)", fontWeight: 700 }}>Åpne →</span>
      </a>

      {/* User Profile Card */}
      <div style={{ background: "var(--surface)", borderRadius: "14px", padding: "14px", border: "1px solid var(--divider)", marginTop: "12px", display: "flex", alignItems: "center", justifyContent: "space-between" }}>
        <div style={{ display: "flex", alignItems: "center", gap: "12px" }}>
          <div style={{
            width: "44px", height: "44px", borderRadius: "12px",
            background: user?.role === "admin" ? "rgba(245,158,11,0.15)" : "rgba(74,222,111,0.1)",
            border: `1px solid ${user?.role === "admin" ? "rgba(245,158,11,0.3)" : "rgba(0,135,81,0.15)"}`,
            display: "flex", alignItems: "center", justifyContent: "center",
            fontSize: "14px", fontWeight: 800, color: user?.role === "admin" ? "var(--accent-orange)" : "var(--accent-green)",
          }}>{user?.avatar}</div>
          <div>
            <div style={{ fontSize: "14px", fontWeight: 700, color: "var(--text-primary)" }}>{user?.name}</div>
            <div style={{ fontSize: "11px", color: "var(--text-muted)" }}>{user?.role === "admin" ? "👑 Administrator" : `Ansatt #${user?.id}`}</div>
          </div>
        </div>
        <button onClick={logout} style={{
          fontSize: "12px", color: "var(--accent-red)", background: "rgba(238,39,55,0.08)",
          border: "1px solid rgba(239,68,68,0.2)", borderRadius: "10px", padding: "8px 14px",
          cursor: "pointer", fontWeight: 700,
        }}>Logg ut</button>
      </div>
    </div>
  );
}

const PAGES = [
  { key:"hjem", label:"Hjem", iconKey:"hjem" },
  { key:"sjekk", label:"Sjekkliste", iconKey:"sjekk" },
  { key:"ordre", label:"Bestilling", iconKey:"ordre" },
  { key:"vakt", label:"Tid", iconKey:"vakt" },
  { key:"rapport", label:"Rapport", iconKey:"rapport" },
  { key:"chat", label:"Chat", iconKey:"chat" },
];

function LoginPage({ onLogin }) {
  const [step, setStep] = useState("select");
  const [selectedUser, setSelectedUser] = useState(null);
  const [pin, setPin] = useState("");
  const [error, setError] = useState("");

  const addDigit = (d) => {
    if (pin.length < 4) {
      const next = pin + d;
      setPin(next);
      if (next.length === 4) {
        setTimeout(() => {
          if (next === selectedUser.pin) { onLogin(selectedUser); }
          else { setError("Feil PIN-kode. Prøv igjen."); setPin(""); }
        }, 250);
      }
    }
  };

  return (
    <div style={{ minHeight:"100vh", background:"#F4F5F7", fontFamily:"'Nunito', sans-serif", maxWidth:"480px", margin:"0 auto" }}>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Nunito:wght@500;600;700;800;900&display=swap');
        * { box-sizing:border-box; margin:0; padding:0; }
        @keyframes fadeUp { from { opacity:0; transform:translateY(14px); } to { opacity:1; transform:translateY(0); } }
        @keyframes dotPop { 0% { transform:scale(0); } 60% { transform:scale(1.3); } 100% { transform:scale(1); } }
        @keyframes glow { 0%,100% { box-shadow: 0 0 20px rgba(0,135,81,0.15); } 50% { box-shadow: 0 0 40px rgba(0,135,81,0.25); } }
      `}</style>

      {/* Green header */}
      <div style={{ background:"linear-gradient(135deg, #008751, #00A86B)", padding:"40px 24px 28px", borderRadius:"0 0 28px 28px", textAlign:"center", position:"relative", overflow:"hidden" }}>
        <div style={{ position:"absolute", top:"-20px", right:"-10px", width:"100px", height:"100px", borderRadius:"50%", background:"rgba(255,255,255,0.08)" }}/>
        <div style={{ position:"absolute", bottom:"-30px", left:"20px", width:"80px", height:"80px", borderRadius:"50%", background:"rgba(255,255,255,0.05)" }}/>
        <img src={LOGO} alt="7-Eleven" style={{ width:"100px", height:"auto", filter:"drop-shadow(0 4px 12px rgba(0,0,0,0.2))", position:"relative" }}/>
        <div style={{ marginTop:"10px", display:"inline-block", background:"rgba(255,255,255,0.2)", borderRadius:"20px", padding:"3px 14px" }}>
          <span style={{ fontSize:"12px", fontWeight:900, color:"#fff", letterSpacing:"0.15em" }}>HUB</span>
        </div>
      </div>

      <div style={{ padding:"24px" }}>
        {step === "select" ? (
          <div style={{ animation:"fadeUp 0.4s ease" }}>
            <h2 style={{ fontSize:"22px", fontWeight:900, color:"#1A1D23", textAlign:"center", marginBottom:"4px" }}>Velkommen!</h2>
            <p style={{ fontSize:"14px", color:"#9BA1AD", textAlign:"center", marginBottom:"20px" }}>Hvem logger inn?</p>
            <div style={{ display:"flex", flexDirection:"column", gap:"8px" }}>
              {STAFF.map((user, i) => (
                <button key={user.id} onClick={() => { setSelectedUser(user); setStep("pin"); setPin(""); setError(""); }}
                  style={{
                    display:"flex", alignItems:"center", gap:"14px", width:"100%", padding:"14px 16px",
                    background:"#FFFFFF", border:"1px solid #E8EAEE", borderRadius:"16px", cursor:"pointer", textAlign:"left",
                    boxShadow:"0 2px 8px rgba(0,0,0,0.04)", animation:`fadeUp 0.4s ease ${i*0.04}s both`,
                  }}>
                  <div style={{
                    width:"44px", height:"44px", borderRadius:"12px",
                    background: user.role==="admin" ? "#FFF3E0" : "#E6F5ED",
                    display:"flex", alignItems:"center", justifyContent:"center",
                    fontSize:"14px", fontWeight:900, color: user.role==="admin" ? "#F7941E" : "#008751",
                  }}>{user.avatar}</div>
                  <div style={{ flex:1 }}>
                    <div style={{ fontSize:"15px", fontWeight:800, color:"#1A1D23" }}>{user.name}</div>
                    <div style={{ fontSize:"12px", color:"#9BA1AD" }}>{user.role==="admin" ? "👑 Admin" : `Ansatt #${user.id}`}</div>
                  </div>
                  <svg width="20" height="20" viewBox="0 0 20 20" fill="none"><path d="M7.5 5l5 5-5 5" stroke="#9BA1AD" strokeWidth="1.5" strokeLinecap="round"/></svg>
                </button>
              ))}
            </div>
          </div>
        ) : (
          <div style={{ animation:"fadeUp 0.3s ease", textAlign:"center" }}>
            <button onClick={() => { setStep("select"); setPin(""); setError(""); }}
              style={{ background:"none", border:"none", color:"#008751", fontSize:"14px", fontWeight:700, cursor:"pointer", marginBottom:"20px" }}>← Tilbake</button>
            <div style={{
              width:"80px", height:"80px", borderRadius:"20px", margin:"0 auto 16px",
              background: selectedUser?.role==="admin" ? "#FFF3E0" : "#E6F5ED",
              border:`3px solid ${selectedUser?.role==="admin" ? "#F7941E" : "#008751"}`,
              display:"flex", alignItems:"center", justifyContent:"center",
              fontSize:"24px", fontWeight:900, color: selectedUser?.role==="admin" ? "#F7941E" : "#008751",
              animation:"glow 3s ease infinite",
            }}>{selectedUser?.avatar}</div>
            <div style={{ fontSize:"20px", fontWeight:900, color:"#1A1D23" }}>{selectedUser?.name}</div>
            <div style={{ fontSize:"13px", color:"#9BA1AD", marginTop:"4px", marginBottom:"24px" }}>Tast din 4-sifrede PIN</div>
            <div style={{ display:"flex", gap:"16px", justifyContent:"center", marginBottom:"8px" }}>
              {[0,1,2,3].map(i => (
                <div key={i} style={{
                  width:"20px", height:"20px", borderRadius:"50%",
                  background: i < pin.length ? "#008751" : "#E8EAEE",
                  transition:"all 0.15s", animation: i < pin.length ? "dotPop 0.25s ease" : "none",
                  boxShadow: i < pin.length ? "0 0 10px rgba(0,135,81,0.3)" : "none",
                }}/>
              ))}
            </div>
            {error && <div style={{ fontSize:"13px", color:"#EE2737", fontWeight:700, marginBottom:"4px" }}>{error}</div>}
            <div style={{ display:"grid", gridTemplateColumns:"repeat(3,1fr)", gap:"10px", maxWidth:"280px", margin:"20px auto 0" }}>
              {[1,2,3,4,5,6,7,8,9,null,0,"⌫"].map((d,i) => (
                d === null ? <div key={i}/> : (
                  <button key={i} onClick={() => d==="⌫" ? setPin(p=>p.slice(0,-1)) : addDigit(String(d))}
                    style={{
                      aspectRatio:"1.2", borderRadius:"16px", border:"1px solid #E8EAEE",
                      background:"#FFFFFF", color: d==="⌫" ? "#EE2737" : "#1A1D23",
                      fontSize: d==="⌫" ? "18px" : "28px", fontWeight:800, cursor:"pointer",
                      boxShadow:"0 2px 8px rgba(0,0,0,0.04)", display:"flex", alignItems:"center", justifyContent:"center",
                    }}>{d}</button>
                )
              ))}
            </div>
          </div>
        )}
      </div>
    </div>
  );
}

export default function App() {
  const [user, setUser] = useState(null);
  const [page, setPage] = useState("hjem");
  const [allChecked, setAllChecked] = useState({});
  const now = new Date();

  // Per-user checked state
  const checked = user ? (allChecked[user.id] || { apning:{}, start:{}, slutt:{} }) : { apning:{}, start:{}, slutt:{} };
  const setChecked = (fn) => {
    setAllChecked(prev => ({
      ...prev,
      [user.id]: typeof fn === "function" ? fn(prev[user.id] || { apning:{}, start:{}, slutt:{} }) : fn
    }));
  };

  const logout = () => { setUser(null); setPage("hjem"); };

  if (!user) {
    return <LoginPage onLogin={(u) => setUser(u)} />;
  }

  return (
    <div style={{ minHeight:"100vh", background:"var(--bg)", fontFamily:"var(--font)", maxWidth:"480px", margin:"0 auto" }}>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Nunito:wght@500;600;700;800;900&display=swap');
        :root {
          --bg:#F4F5F7; --surface:#FFFFFF; --task-bg:#F0F1F4; --task-done-bg:#E8F5E9;
          --text-primary:#1A1D23; --text-secondary:#5A5F6B; --text-done:#9BA1AD; --text-muted:#9BA1AD;
          --accent-green:#008751; --accent-orange:#F7941E; --accent-red:#EE2737;
          --ring-bg:#E0E3E8; --check-border:#C8CDD4; --badge-bg:#F0F1F4; --divider:#E8EAEE;
          --font: 'Nunito', sans-serif;
        }
        * { box-sizing:border-box; margin:0; padding:0; }
        input, textarea, select { font-family: var(--font); }
        input::placeholder, textarea::placeholder { color: var(--text-muted); }
        ::-webkit-scrollbar { width: 0; height: 0; }
        @keyframes pulse { 0%, 100% { opacity: 1; } 50% { opacity: 0.4; } }
        @keyframes fadeIn { from { opacity:0; transform:translateY(8px); } to { opacity:1; transform:translateY(0); } }
        @keyframes fadeUp { from { opacity:0; transform:translateY(14px); } to { opacity:1; transform:translateY(0); } }
        @keyframes dotPop { 0% { transform:scale(0); } 60% { transform:scale(1.3); } 100% { transform:scale(1); } }
        @keyframes glow { 0%,100% { box-shadow: 0 0 20px rgba(0,135,81,0.15); } 50% { box-shadow: 0 0 40px rgba(0,135,81,0.25); } }
      `}</style>

      {/* Header — hidden on home page */}
      {page !== "hjem" && (
        <div style={{ background:"#008751", padding:"16px 20px 14px", display:"flex", alignItems:"center", justifyContent:"space-between" }}>
          <div style={{ display:"flex", alignItems:"center", gap:"10px" }}>
            <button onClick={()=>setPage("hjem")} style={{ background:"rgba(255,255,255,0.2)", border:"none", borderRadius:"8px", padding:"6px 8px", cursor:"pointer", display:"flex" }}>
              <svg width="18" height="18" viewBox="0 0 18 18" fill="none"><path d="M11 4L6 9l5 5" stroke="#fff" strokeWidth="2" strokeLinecap="round"/></svg>
            </button>
            <div>
              <div style={{ fontSize:"10px", fontWeight:800, color:"rgba(255,255,255,0.7)", letterSpacing:"0.1em" }}>7-ELEVEN HUB</div>
              <div style={{ fontSize:"18px", fontWeight:900, color:"#fff", fontFamily:"var(--font)" }}>{PAGES.find(p=>p.key===page)?.label || "Opplæring"}</div>
            </div>
          </div>
          <div style={{ display:"flex", alignItems:"center", gap:"8px" }}>
            <img src={LOGO} alt="" style={{ width:"32px", height:"auto" }}/>
            <button onClick={logout} style={{ background:"rgba(255,255,255,0.2)", border:"none", borderRadius:"8px", padding:"5px 8px", cursor:"pointer" }}>
              <div style={{ width:"26px", height:"26px", borderRadius:"7px", background:"rgba(255,255,255,0.3)", display:"flex", alignItems:"center", justifyContent:"center", fontSize:"9px", fontWeight:900, color:"#fff" }}>{user?.avatar}</div>
            </button>
          </div>
        </div>
      )}

      {/* Content */}
      <div style={{ padding:"16px 16px 120px" }}>
        {page==="hjem" && <HomePage setPage={setPage} checked={checked} user={user} logout={logout}/>}
        {page==="sjekk" && <ChecklistPage checked={checked} setChecked={setChecked}/>}
        {page==="ordre" && <OrdrePage/>}
        {page==="vakt" && <TidPage/>}
        {page==="rapport" && <ReportPage/>}
        {page==="laering" && <TrainingPage/>}
        {page==="chat" && <ChatPage/>}
      </div>

      {/* Bottom Nav */}
      <div style={{
        position:"fixed", bottom:0, left:"50%", transform:"translateX(-50%)", width:"100%", maxWidth:"480px",
        background:"#FFFFFF", borderTop:"1px solid var(--divider)",
        display:"flex", justifyContent:"space-around", padding:"6px 4px 22px", zIndex:100,
        boxShadow:"0 -4px 20px rgba(0,0,0,0.05)",
      }}>
        {PAGES.map(p => {
          const active = page === p.key;
          return (
            <button key={p.key} onClick={()=>setPage(p.key)} style={{
              background:"none", border:"none", cursor:"pointer",
              display:"flex", flexDirection:"column", alignItems:"center", gap:"3px", padding:"4px 2px", minWidth: "50px",
            }}>
              {NavIcons[p.iconKey](active)}
              <span style={{ fontSize:"9.5px", fontWeight:active?700:500, color: active?"var(--accent-green)":"var(--text-muted)", letterSpacing:"0.02em" }}>{p.label}</span>
              {active && <div style={{ width:"4px", height:"4px", borderRadius:"50%", background:"var(--accent-green)" }}/>}
            </button>
          );
        })}
      </div>
    </div>
  );
}
