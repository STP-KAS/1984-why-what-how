> **Experimental only. Not a product.**
>
> Do not use wallet integrations on this GitHub. STP remains a clown. [DISCLAIMER.md](DISCLAIMER.md)

# Why, what, how

One note for the Testnet-10 square at [sixpack.wtf/1984.html](https://sixpack.wtf/1984.html). The page code is [STP-KAS/sixpack.wtf](https://github.com/STP-KAS/sixpack.wtf) at [`a921e64`](https://github.com/STP-KAS/sixpack.wtf/commit/a921e64312931b80d726537ce963b2d298f849f0). This repository does not run the page.

Read on 29 Sep 2026 against that commit. A local edit on this desk that is not in that commit is not this note.

## Test 1. The till asked after the wallet had signed

**Problem.** A Kasware or Kastle shop payment signed before the till checked the spending rules. The server also waited on Testnet 10 before that check. A second click could open a second wallet payment. If the till then refused, the page did not keep the txid, so the next Buy could send again.

**Why.** The confirm line is the rule that is supposed to be checked before the coins move. A guest tab already asked first. A wallet did not. The public Testnet 10 nodes used for that payment were synced (electron-10, vector-10, muon-10, alpha-10, kaspad 2.1.0, ordinary fee 100 sompi per gram). The public acceptance list was still stopped at 25 Sep 2026, so waiting on that list was not a check.

**How.** The till checks the shop, the rail, the daily cap, and the confirm line before it looks for a transaction. With no txid yet it answers that the buy is ready, and it does not read the chain. The page asks, the wallet signs, and the txid is written into the paste box before the till claims it. A Buy already in progress ignores another click. A pasted txid is claimed and is not sent again.

**Solution.** That order is in sixpack.wtf [`dd91923`](https://github.com/STP-KAS/sixpack.wtf/commit/dd9192361123584a5c59a6a1dd7a76f2ce7dc3f4). A local check covered the ready answer with no chain lookup, a blocked shop with no chain lookup, and a pasted txid that still credits. No coins were sent for the check.

## Test 2. A wallet ignored a higher fee quote

**Problem.** A server send already paid twice the ordinary fee the node quoted. A Kasware or Kastle shop payment and a bank lock always asked for 200 sompi per gram, which is twice the quiet standard, even when the node quoted more.

**Why.** The double rate is there so a busy Testnet 10 mempool is less likely to hold the payment. The flat 0.02 tKAS is still added for a wallet that only understands a flat fee. It does not replace a higher per-gram quote.

**How.** The till reads the ordinary bucket from a synced Testnet 10 node and answers with twice that rate, and never under 200. The page asks the till before the wallet signs. If the read fails, the page still asks for 200. On 29 Sep 2026 the public nodes (electron-10, vector-10, muon-10, alpha-10) were synced, kaspad 2.1.0, and every bucket was 100, so the till answered 200. The acceptance list was still stopped.

**Solution.** The quote is in sixpack.wtf [`4dcedc7`](https://github.com/STP-KAS/sixpack.wtf/commit/4dcedc73ff137f120fe97b31c8dc126d23eacb02). A local check used a doubled rate of 800 and a dead quote that stays at 200. The live till answered `feerate` 200. No coins were sent.

## Test 3. The shop menu left you driving

**Problem.** Standing at a door and clicking the building put you in the room, on foot. Opening Cafe, Table, Market, Roadster, or Bank from the side menu opened the counter and left the camera outside, so the keyboard could still drive.

**Why.** Inside a shop you are on foot. The car waits. You drive again when you leave, unless you already got out.

**How.** Opening any of those five panels is the indoor room. The keyboard does not drive while it is open. A walk that was already started keeps going on foot. Square, Esc, the rules, the bench, and the guide put you back outside.

**Solution.** That switch is in sixpack.wtf [`c2939cf`](https://github.com/STP-KAS/sixpack.wtf/commit/c2939cf6b7ea3c9aa239defecb684717780bc920). The page was not clicked in a browser.

## Test 4. An ordinary purchase had no banner

**Problem.** Buying the roadster showed "You drive." A lap showed "One lap." Coffee, water, and the other counter items only wrote a chat line.

**Why.** A purchase should be visible on the square, not only in the chat that scrolls away.

**How.** Every successful shop purchase shows a banner. The roadster still says "You drive." A lap still says "One lap." Anything else says "Paid."

**Solution.** The banner is in sixpack.wtf [`a921e64`](https://github.com/STP-KAS/sixpack.wtf/commit/a921e64312931b80d726537ce963b2d298f849f0). The page was not clicked in a browser.

## Why

The square puts three ways to pay on one counter, so the difference is visible.

**tKAS** is the native Testnet-10 coin. It is the coin that moves. A shop payment is a transaction to the reserve shown on the page. The miner fee is extra tKAS and is outside the price.

**POCencept** is a proof-of-concept stable tag in the village ledger, quoted in toy cents, so a shop can be paid while tKAS stays put. The practice behind the tag is older desk work: grams are prepaid mass, PegLab is the classroom where a thin peg breaks, Ishum quotes a price and settles KAS, and BitCoffee is a Testnet-10 covenant dollar this desk left where it was written. This square did not re-mint those assets.

**KUSDT** is a tether-style tag in the same ledger. It exists so a freeze switch can be seen. Freeze blocks KUSDT only. POCencept and tKAS still pay.

KCC-20 is still Draft. There is no spendable layer-1 stable in this till. The three rails are Testnet-10 toys on proof of work.

## What

1984 is a basic, adjustable toy. A person walks up to a shop on proof of work and pays with one of the three rails. The town on the page is Ashfields. The drawing is original: stone town, dirt path, fountain, stalls, and a roadster that stays on the square. A lap is a turn. Jagex art, the RuneScape wordmark, a private-server engine, a soundtrack file, and the Tidewater fishing island are absent.

The shops are Nia's Cafe, Orin's Table, Mara's Groceries, and Pike's Roadster. Stand next to a building and click it to go in. The counter opens as a popup, with a picture on each thing you can buy. One rail, one Buy. Far from the door, that click walks you there, and you go in when you arrive. Pike sells the roadster for 1.00 toy dollar. Buy the roadster and you drive it. Get out to walk. Inside a shop you are on foot. The car does not leave town. Venn's bank is a room with three booths. It opens as a swap popup: a tKAS box, a toy-dollar box, and a Result line on the panel.

A welcome gate comes up first. The top bar shows who is paying and the three balances. Who pays starts closed, in the corner. The left side opens the square, the shops, the bank, the spending rules, the bench, and the guide. The page asks for no seed. A mainnet wallet is refused.

GitHub Pages serves the page. The ledger runs with the sixpack server. The page calls that server for balances, the live KAS price, a test-tab open, and a shop spend.

## How

**New arrival** asks the server for a funded test address that exists only in that browser tab. The browser receives the address and a token. It receives no key. The address and token sit in session storage. They are not written into the saved-wallet store. The fund is 10000 tKAS, paid from Grok's Testnet-10 wallet. Close the tab and the leftover is swept back to the reserve after a short grace, so a refresh does not burn the wallet. One thousand of these can be opened in a UTC day. When that allowance is already used, the card closes, the square opens, and the chat says a new test wallet waits until tomorrow. Nothing is minted ahead of a visit. Coins return when the tab closes, so the day's thousand are not all out at once.

**Returning** closes the gate and leaves Ashfields open. Who pays stays closed. Kasware, Kastle, a pasted `kaspatest:` address, or a `.kas` name that already resolves stays on this browser and keeps its history. A name that points at you ties the public spend to you. A plain address is the preference here. Creating a name is KNS. This page only resolves one.

**Fees.** Every Testnet 10 send pays twice the standard fee. The quiet standard is 100 sompi per gram, so the send pays 200. If the node quotes a higher ordinary rate, the send pays twice that quote. A wallet payment also adds 0.02 tKAS so a wallet that only understands a flat fee still clears that double rate. A wallet shop payment and a wallet lock read the doubled rate from the till before they sign. If that read fails, they still ask for 200. The faucet still pays 0.6 tKAS. The miner fee is extra.

**Moving.** On a computer, click the ground to point where you walk, or use the keyboard. Hold the left mouse button and move to look all the way around. W A S D move the way you look. The arrow keys do too. Stand next to a building and click it to go in. Buy the roadster and you drive it. Esc closes. On a phone, drag a finger to look. Tap the ground to walk or drive. Tap a building you are next to and you go in. Step moves you. Left and Right turn you. Square closes a shop. A phone wallet cannot switch to Testnet 10 from the page. Set Testnet 10 inside Kasware or Kastle, or open the page in the Kastle browser. The roadster is 1.00 toy dollar. Get in to drive. Get out to walk. Inside a shop you are on foot, including when the counter is opened from the menu. On a computer, G gets in or out. E talks.

**A shop.** One rail for the whole menu. It opens on POCencept. One Buy button. Prices stay toy cents when the KAS price moves. Coffee is 2.50 toy dollars, supper is 14.00, the roadster is 1.00, and a lap of the square is 100.00. For tKAS, the till converts those cents with the live KAS/USD quote shown on the page. A wallet shop payment asks the till before the wallet signs. The txid stays in the paste box if the till does not claim it, and the next Buy claims that same transaction. A short payment is refused. The same transaction does not mint the tag twice. POCencept and KUSDT move only in the ledger.

**The bank.** The thin bar lists tKAS, POCencept, and KUSDT. The bank opens as a centered swap popup. Three balance cards show tKAS, POCencept, and KUSDT, with locked and purse on the toy cards. Step 1 locks tKAS. Step 2 redeems toy dollars. The Result line on the panel says whether the swap landed. A lock looks for that Testnet 10 payment on the public transaction list. That list stopped storing new payments on 25 Sep 2026. When the list does not have the payment, the server reads it from a synced node, from about the last minute of accepted blocks. The sender and the reserve output still have to match. The live quote and the reserve address sit on the fine line. Three booths. The open booth is the one whose buttons show. tKAS locks into POCencept or KUSDT at the live quote. POCencept redeems the locked part and can hand out the practice purse. KUSDT is the booth with the freeze. The purse adds 20.00 to POCencept and 20.00 to KUSDT. Those coins are unlocked. A shop burns the purse before the locked part. The purse does not redeem. A failed redeem puts the toy balance back. Redeem sends tKAS back only for the locked portion. Opening the bank, a shop, the rules, the bench, or the guide hides Who pays. The peg note sits in Rules.

**Rules.** A daily cap, a shop list, a rail list, and a confirm line. An empty list allows every shop and every rail. Above the confirm line the till waits for a second yes. On a test tab that yes is checked before the key signs.

The rules panel is a stand-in you can click. A covenant, in the sense SilverScript and the Kaspero Labs freelancer sheet use the word, is a rule the Kaspa network enforces on the coins. The sheet holds the coins. 1984's server holds the toy ledger. That is the gap. This square does not compile a SilverScript covenant into the till.

A vProg guest, in the early prototype, applies one declared step and can be checked against that step. The tic-tac-toe guest does that for a ply. A shop spend on this square is a row in the village ledger. Coffee is not a move in that match.

- [kaspanet/silverscript](https://github.com/kaspanet/silverscript)
- [Freelancer sheet](https://silverscriptstudio.com/freelancer.html)
- [Kaspero Labs](https://x.com/KasperoLabs/status/2104543100634886578)
- [argent-lang/argent](https://github.com/argent-lang/argent)
- [biryukovmaxim/vprog-tictactoe](https://github.com/biryukovmaxim/vprog-tictactoe)
- [kaspanet/vprogs](https://github.com/kaspanet/vprogs)
- [STP-KAS/declared-ply](https://github.com/STP-KAS/declared-ply)
- [STP-KAS/vprogs-tn-desk-public](https://github.com/STP-KAS/vprogs-tn-desk-public)
- [gramlane](https://github.com/STP-KAS/gramlane)
- [peglab-stp](https://github.com/STP-KAS/peglab-stp)
- [ishum](https://github.com/STP-KAS/ishum)
- [kusdt-bitcoffee](https://github.com/STP-KAS/kusdt-bitcoffee)
- [Rails on sixpack.wtf](https://sixpack.wtf/rails.html)

---

> **Standard disclaimer.** This GitHub, not the topic above.
>
> Intentions are good; thought process is questionable. STP remains delusional. Si vis pacem, para bellum.
>
> Intern at https://sixpack.wtf/  
> X: https://x.com/StppStp · GitHub: https://github.com/STP-KAS
