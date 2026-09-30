> **Experimental only. Not a product.**
>
> Do not use wallet integrations on this GitHub. STP remains a clown. [DISCLAIMER.md](DISCLAIMER.md)

# Why, what, how

One note for the Testnet-10 square at [sixpack.wtf/1984.html](https://sixpack.wtf/1984.html). The page code is [STP-KAS/sixpack.wtf](https://github.com/STP-KAS/sixpack.wtf) at [`3d87805`](https://github.com/STP-KAS/sixpack.wtf/commit/3d87805390b84dabb9b7cde89863718551fa9e6a). This repository does not run the page.

Read on 30 Sep 2026 against that commit. A local edit on this desk that is not in that commit is not this note.

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

## Kasware lock

**Problem.** The bank showed a Testnet 10 balance, and Lock answered: log in with Kasware or Kastle, or paste a txid. Nothing was sent. The page only asked the wallet when the saved login was already marked Kasware or Kastle. A pasted address, or a Kasware account on that same address whose helper script was not the signer, stopped before the wallet opened.

**Why.** The balance comes from the address. The signature has to come from the wallet that holds that address. Those are not the same check.

**How.** Lock asks Kasware or Kastle when that wallet's account is the address on the page. A saved Kasware login still signs if the extension is in the tab, even when the helper script is missing. A different address does not sign. A mainnet account does not sign. The txid is kept in the paste box if the till does not claim it, and the next Lock claims that same transaction.

**Solution.** That check is in sixpack.wtf [`c170fde`](https://github.com/STP-KAS/sixpack.wtf/commit/c170fde1071d38a9b03c2ae2edc62af3992f4ffa). The page was not clicked in a browser. No coins were sent for the check.

## Clerks, and the roadster in front of the shop

**Problem.** The bank showed locked and purse on the same cards as the swap. Changing tKAS into KUSDT meant finding which box was which. The three booth signs sat behind the popup. Kasware opened with one waiting line. The roadster stayed where you got out.

**Why.** Locked toy dollars came from a real tKAS send and can come back. The purse is practice and spends in the shops. Those piles still have to stay apart. The everyday swap does not need both numbers on the first screen. A swap between POCencept and KUSDT can move each pile as itself, so no extra tKAS is locked or freed.

**How.** The bank opens on three clerks. Push tKAS, POCencept, or KUSDT. The open clerk swaps into the other two. The books desk shows locked and purse, says why, and holds the practice purse and the KUSDT freeze. While Kasware is opening, the clerk lists the steps: checking the amount, opening the wallet, the approval, Testnet 10, and the tag. The owned roadster parks in front of Pike's shop. Click it to get in. If you are far, you walk there first. Get out and it goes back. Thrusters show only while it is moving.

**Solution.** That is in sixpack.wtf [`1d2153a`](https://github.com/STP-KAS/sixpack.wtf/commit/1d2153a29f38b7b0164874c9c58773e2ab13ebe6). A local check moved a purse amount without creating a locked balance, then moved an amount that crossed into the locked pile and left the liability unchanged. A frozen KUSDT blocked both directions. The remaining locked pile still redeemed, and the purse still did not. The page was not clicked in a browser. No coins were sent for the check.

## The page asks before a buy

**Problem.** Logged in with Kasware, a shop buy asked the wallet to sign. A POCencept swap and a KUSDT swap do not move tKAS out of that wallet.

**Why.** The wallet holds the tKAS. The page holds the toy tags. A shop buy and a toy swap can be confirmed on the page. The wallet signs when tKAS leaves it.

**How.** Buy opens a card on the page: you want to buy this for that price, then OK. Not now leaves the balance. A POCencept or KUSDT swap opens the same kind of card. The wallet opens only for a tKAS swap at the bank. With Kasware or Kastle logged in, the shop's tKAS rail does not sign. A new arrival is funded with 50000 tKAS. None were open, so none were sent ahead of a visit.

**Solution.** That is in sixpack.wtf [`8df68fc`](https://github.com/STP-KAS/sixpack.wtf/commit/8df68fc849ad6a3fcbc7808fad33b348bbe9fea3). Fifty-eight local checks passed. The page was not clicked in a browser. No test wallet was minted for the check.

## You walk into the room

**Problem.** Clicking a building opened the buy card at the same moment as the room. The cafe was one counter. The bank opened the swap before anyone pushed a clerk.

**Why.** The room is the place. The card is the till. Walking in and paying are two steps.

**How.** You walk in and the card stays shut. The bank card opens when you click a clerk. The books desk opens from the books. In the cafe, and at the table, you sit, then click the menu on the wall or the card on the table. The market opens when you click the counter. The showroom opens when you click Pike or the sign. Esc closes the card and leaves you in the room. Esc again, or Square, leaves. The buildings have more trim, and each room has its own furniture. Prices, the walk grid, and who signs are unchanged.

**Solution.** That is in sixpack.wtf [`532e663`](https://github.com/STP-KAS/sixpack.wtf/commit/532e66300576f3fb1e54b16884f953af1d6655ae). Sixty-two local checks passed. The page was not clicked in a browser. No coins were sent for the check.

## The card kept the old balances

**Problem.** A shop buy landed in the till and the banner said Paid. The three numbers on the open card stayed where they were, so the next click paid again.

**Why.** The till had already taken the cents. The card was drawn when it opened and was not drawn again after the payment.

**How.** The payment's answer is written onto the open card at once, and the card is drawn again from the till. The top bar uses the same numbers. The bank card already did this. A cafe, table, market, or showroom card does it too.

**Solution.** That redraw is in sixpack.wtf [`94fb455`](https://github.com/STP-KAS/sixpack.wtf/commit/94fb4553fb22557f4606b2b09604e45145317916). Sixty-three local checks passed. The page was not clicked in a browser. No new coins were sent for the check.

## The doorway was a hard cut

**Problem.** Walking in swapped the town for the room in one frame. The long outdoor note stayed on the screen. Every chair, clerk, and card looked the same, so the first click often missed.

**Why.** A doorway should show one next step. A paragraph, and a pile of targets, hide that step.

**How.** The view fades through black. The outdoor note hides while you are inside. The chat says one line: click a clerk, take a seat, click the counter, or click Pike or the sign. A gold ring marks that thing. After you sit, the ring moves to the menu and the card on the table. Closing the card does not repeat the line. The card still waits until you use the counter. Prices, the walk grid, and who signs are unchanged.

**Solution.** That entry is in sixpack.wtf [`0e86db4`](https://github.com/STP-KAS/sixpack.wtf/commit/0e86db445f84444144119ecad0051ace2934fa55). Sixty-four local checks passed. The page was not clicked in a browser. No coins were sent for the check.

## The test wallet sat on one line

**Problem.** New arrival stayed on one line, Opening a test wallet, and the tab never got a wallet.

**Why.** The coins behind that gift are split into millions of small pieces. Putting 50000 tKAS together takes many joins. The page waited on one request and gave up while that work was still running. The line did not say which part was running.

**How.** The page starts the open and then reads the step. If it is still going after a moment, the gate lists checking today's wallets, making the address, connecting, gathering the coins, putting the coins together with the count, signing, and broadcasting. Leave the tab open. A fast open still closes the gate. The gift stays 50000 tKAS. Prices, the walk grid, who signs, and the 0.6 faucet cap stay as they are.

**Solution.** That wait is in sixpack.wtf [`ab1981d`](https://github.com/STP-KAS/sixpack.wtf/commit/ab1981df47e6cd6df3e3faa057a6224b1e1b276e). Seventy local checks passed. One open on this desk finished in about 23 seconds, showed those steps, funded 50000 tKAS, and the tab was closed so the coins return. The page was not clicked in a browser.

## Each window said its name twice

**Problem.** In the bank, tKAS, POCencept, and KUSDT each sat on two signs, one above the other.

**Why.** The window and the clerk were both saying the same name. One sign is enough to know which clerk to push.

**How.** The extra sign on the window is gone. The clerk keeps the name. Pushing that clerk still opens the booth. The outdoor walking note still hides once you are inside. Prices, the walk grid, who signs, and the 50000 tKAS gift stay as they are.

**Solution.** That is in sixpack.wtf [`916bdf8`](https://github.com/STP-KAS/sixpack.wtf/commit/916bdf8d989cb9dd5a39bd93997d352859487e1c). Seventy local checks passed. The page was not clicked in a browser. No coins were sent for the check.

## The roadster can ride a ship

**Problem.** The car stayed in town. There was no way to leave the square in it.

**Why.** A launch should be a ride you can watch: engines, liftoff, the booster letting go, orbit, then the car leaving the ship. Ending it should say there is no return, then offer a way back after a wait.

**How.** Launch shows when you own the car, you are in it, and you are outside. The ride is free. The 1.00 price stays. The ship climbs, the booster drops, and the car slides out nose-first. One line at a time names the moment. End the flight and the view goes dark: No return policy. You remain in the dark. Enjoy space. Thanks for using SpaceX services. After five seconds, Simulation theory puts you back on the square in the car. Prices, the walk grid, who signs, the one name on each bank window, and the 50000 tKAS gift stay as they are.

**Solution.** That ride is in sixpack.wtf [`e17af49`](https://github.com/STP-KAS/sixpack.wtf/commit/e17af49b1477dee3a213e76c78e8ce1923456476). Seventy-two local checks passed. The page was not clicked in a browser. No coins were sent for the check.

## The car started in the seat

**Problem.** Buying the keys put you in the seat. Get out sat with Left, Step, and Right, so leaving the car was easy to miss.

**Why.** The car should be waiting on a lot, ready to jump in. Getting out should be its own button.

**How.** Three stalls sit on the cobble in front of Pike's shop. The roadster waits in the middle one, nose toward the square. Buying the keys says Parked and leaves you beside it. Click the car, or Get in, to drive. Get in says You drive. Get out is the gold button. While you drive it sits beside Launch. Getting out puts the car back on the lot. The 1.00 price, the walk grid, who signs, the ship ride, the one name on each bank window, and the 50000 tKAS gift stay as they are.

**Solution.** That lot is in sixpack.wtf [`8cdba0c`](https://github.com/STP-KAS/sixpack.wtf/commit/8cdba0ca3558af882afd81a9eb3d337f7f5db4f9). Seventy-two local checks passed. The page was not clicked in a browser. No coins were sent for the check.

## The end showed before the car was out

**Problem.** Simulation theory sat on the flight from the start. The end line could show while the car was still in the rocket. There was no bar. A hop past orbit was not a payment. In the cafe and at the table the only path was a seat. The card on the table looked like a payment grid and did not say what kind of payment it was.

**Why.** The end belongs after the car is out. Going home is a choice after that end. A hop should be a paid ride with its own bar. A shop should say whether the payment is this square's ledger or a Testnet 10 transaction. The cafe should take a seat or an order at the counter.

**How.** A bar fills from Launch until the car leaves the ship. At the full bar the thanks line shows, with End the flight: No return policy. You remain in the dark. Enjoy space. Thanks for using SpaceX services. Simulation theory shows only after End the flight. That click says you returned to a simulation of a simulation of a simulation, 255524 deep, and puts you back on the square in the roadster. At that full bar the Moon is 2.00 toy dollars, Mars is 5.00, Jupiter is 8.00, and Saturn is 12.00. The launch stays free. The 1.00 keys stay. On a hop the same end waits ten seconds, and that hop has its own bar. The car rolls and nods. The line on the card says space is broad, speed and distance are relative, and an average of 10 blocks per second makes the ride possible. In the cafe, and at the table, you take a seat or you order at the counter. Seated, the menu blinks. Standing, the counter blinks. A shop buy says it is this square's own ledger, with no covenant transaction. It is not Argent or SilverScript, and it is not a vProg tic-tac-toe ply. A tKAS bank swap says it is a Testnet 10 transaction and the txid is the payment. Prices, the walk grid, who signs, the lot, the one name on each bank window, and the 50000 tKAS gift stay as they are.

**Solution.** That flight is in sixpack.wtf [`853510a`](https://github.com/STP-KAS/sixpack.wtf/commit/853510a6f1b663cd2a190f5dd3b564d669859704). Seventy-three local checks passed. The page was not clicked in a browser. No coins were sent for the check.

## The square had no cinema

**Problem.** The Random films and the desk films had no building. There was no seat in front of a screen, and no way to buy a snack while a film ran.

**Why.** A cinema is a room you walk into. The picture should fill the view from a seat, and the next film should start when one ends.

**How.** Lux's cinema is the dark building on the grass west of the lot. The fountain, the spawn, the parking stalls, and the other buildings stay where they are. Take a seat, then the screen. One ticket is 5.00 toy dollars and plays the whole reel: the Random films, then the desk films. The camera sits in a back-row seat and the screen starts. When a film ends, the next one starts. After the last film the reel starts again. Esc leaves the seat and keeps the ticket. Leaving the building clears it. While the reel runs, snacks sit under the picture: popcorn 1.50, beer 2.00, vodka 3.50, and the cocaine and xanax tags at 6.00 and 4.00. Those last two are toy tags on this square's ledger. They are not a real sale. A snack does not stop the film. The ticket and the snacks are this square's own ledger. Prices of the other shops stay as they are. The walk grid changes only on that building's grass.

**Solution.** That cinema is in sixpack.wtf [`3d87805`](https://github.com/STP-KAS/sixpack.wtf/commit/3d87805390b84dabb9b7cde89863718551fa9e6a). Seventy-five local checks passed. The page was not clicked in a browser. No coins were sent for the check.

## Why

The square puts three ways to pay on one counter, so the difference is visible.

**tKAS** is the native Testnet-10 coin. It is the coin that moves. A shop payment is a transaction to the reserve shown on the page. The miner fee is extra tKAS and is outside the price.

**POCencept** is a proof-of-concept stable tag in the village ledger, quoted in toy cents, so a shop can be paid while tKAS stays put. The practice behind the tag is older desk work: grams are prepaid mass, PegLab is the classroom where a thin peg breaks, Ishum quotes a price and settles KAS, and BitCoffee is a Testnet-10 covenant dollar this desk left where it was written. This square did not re-mint those assets.

**KUSDT** is a tether-style tag in the same ledger. It exists so a freeze switch can be seen. Freeze blocks KUSDT only. POCencept and tKAS still pay.

KCC-20 is still Draft. There is no spendable layer-1 stable in this till. The three rails are Testnet-10 toys on proof of work.

## What

1984 is a basic, adjustable toy. A person walks up to a shop on proof of work and pays with one of the three rails. The town on the page is Ashfields. The drawing is original: stone town, dirt path, fountain, stalls, and a roadster. Launch rides a ship to orbit. A bar fills until the car leaves the ship. End the flight shows then. Simulation theory shows only after that click, and it puts you back on the square in the car. A lap is a turn. Jagex art, the RuneScape wordmark, a private-server engine, a soundtrack file, and the Tidewater fishing island are absent.

The shops are Nia's Cafe, Orin's Table, Mara's Groceries, Pike's Roadster, and Lux's Cinema. Stand next to a building and click it to walk in. The card stays shut. The view fades in. The outdoor note hides. A gold ring marks the next step: a clerk, a seat, the counter, or Pike and the sign. After you sit, the ring moves to the menu and the card. In the cafe, and at the table, you take a seat or you order at the counter. Once you are seated, the menu blinks. The counter blinks while you stand. The market opens at the counter. The showroom opens when you click Pike or the sign. Lux's cinema is the dark building west of the lot. Take a seat, then the screen. One ticket of 5.00 toy dollars plays the reel from that seat. Snacks are toy tags while it runs. The bank card opens when you click a clerk. Far from the door, that click walks you there, and you walk in when you arrive. Once the card is open it has one rail, one Buy, and a picture on each thing you can buy. A buy redraws the three balances on that card and on the top bar. Pike sells the roadster for 1.00 toy dollar. It parks on the lot in front of the shop. You stand beside it. Click it, or Get in, to drive. Get out is the gold button, and the car goes back to the lot. Thrusters show while it moves. Inside a shop you are on foot. Launch, while you are in the car and outside, rides a ship to orbit. The car then leaves the ship. A bar fills until the car is out. End the flight shows then, with the thanks line. Simulation theory shows only after that click. At a full bar the Moon is 2.00 toy dollars, Mars is 5.00, Jupiter is 8.00, and Saturn is 12.00. On that hop the same end waits ten seconds, and speed and distance are relative. Lux's cinema is the dark building west of the lot. Take a seat, then the screen. Venn's bank opens on three clerks. Each window says its name once. Push tKAS, POCencept, or KUSDT. The open clerk swaps into the other two. Locked coins and the practice purse are explained in the books desk. The wallet opens only for a tKAS swap. A shop buy, and a POCencept or KUSDT swap, ask on the page first. While that tKAS swap is opening, the steps stay on the clerk.

A welcome gate comes up first. New arrival lists each step while the small coins are joined into the 50000 tKAS gift. The top bar shows who is paying and the three balances. Who pays starts closed, in the corner. The left side opens the square, the shops, the bank, the spending rules, the bench, and the guide. The page asks for no seed. A mainnet wallet is refused.

GitHub Pages serves the page. The ledger runs with the sixpack server. The page calls that server for balances, the live KAS price, a test-tab open, and a shop spend.

## How

**New arrival** asks the server for a funded test address that exists only in that browser tab. The browser receives the address and a token. It receives no key. The address and token sit in session storage. They are not written into the saved-wallet store. The fund is 50000 tKAS, paid from Grok's Testnet-10 wallet. If those coins are in many small pieces, the gate lists each step and the count until Testnet 10 takes the send. Close the tab and the leftover is swept back to the reserve after a short grace, so a refresh does not burn the wallet. One thousand of these can be opened in a UTC day. When that allowance is already used, the card closes, the square opens, and the chat says a new test wallet waits until tomorrow. Nothing is minted ahead of a visit. Coins return when the tab closes, so the day's thousand are not all out at once.

**Returning** closes the gate and leaves Ashfields open. Who pays stays closed. Kasware, Kastle, a pasted `kaspatest:` address, or a `.kas` name that already resolves stays on this browser and keeps its history. A name that points at you ties the public spend to you. A plain address is the preference here. Creating a name is KNS. This page only resolves one.

**Fees.** Every Testnet 10 send pays twice the standard fee. The quiet standard is 100 sompi per gram, so the send pays 200. If the node quotes a higher ordinary rate, the send pays twice that quote. A wallet payment also adds 0.02 tKAS so a wallet that only understands a flat fee still clears that double rate. A wallet shop payment and a wallet lock read the doubled rate from the till before they sign. If that read fails, they still ask for 200. The faucet still pays 0.6 tKAS. The miner fee is extra.

**Moving.** On a computer, click the ground to point where you walk, or use the keyboard. Hold the left mouse button and move to look all the way around. W A S D move the way you look. The arrow keys do too. Stand next to a building and click it to walk in. The card stays shut until you use the counter. Buy the roadster and it parks on the lot. You stand beside it. Esc closes the card, then leaves the room. On a phone, drag a finger to look. Tap the ground to walk or drive. Tap a building you are next to and you walk in. Step moves you. Left and Right turn you. Square leaves the room. A phone wallet cannot switch to Testnet 10 from the page. Set Testnet 10 inside Kasware or Kastle, or open the page in the Kastle browser. The roadster is 1.00 toy dollar. Get in to drive. Get out is the gold button. Inside a shop you are on foot, including when the counter is opened from the menu. On a computer, G gets in or out. E talks. Launch, while you are in the car and outside, rides a ship to orbit. The car then leaves the ship. A bar fills until the car is out. End the flight shows then, with the thanks line. Simulation theory shows only after that click. At a full bar the Moon is 2.00 toy dollars, Mars is 5.00, Jupiter is 8.00, and Saturn is 12.00. On that hop the same end waits ten seconds, and speed and distance are relative. Lux's cinema is the dark building west of the lot. Take a seat, then the screen. The picture fills the view from that seat, and the next film starts when one ends.

**A shop.** One rail for the whole menu. It opens on POCencept. One Buy button. Prices stay toy cents when the KAS price moves. Coffee is 2.50 toy dollars, supper is 14.00, the roadster is 1.00, and a lap of the square is 100.00. The cinema ticket is 5.00. Popcorn is 1.50, beer is 2.00, and vodka is 3.50. The cocaine and xanax lines are toy tags at 6.00 and 4.00, not a real sale. For tKAS, the till converts those cents with the live KAS/USD quote shown on the page. A wallet shop payment asks the till before the wallet signs. The txid stays in the paste box if the till does not claim it, and the next Buy claims that same transaction. A short payment is refused. The same transaction does not mint the tag twice. POCencept and KUSDT move only in the ledger. The shop card says this buy is this square's own ledger. There is no covenant transaction. It is not Argent or SilverScript, and it is not a vProg tic-tac-toe ply. A tKAS bank swap says the txid is the Testnet 10 payment. Walking in fades the view, and a gold ring marks the next step. The open card redraws those balances from the till's answer.

**The bank.** Lock asks Kasware or Kastle when that wallet's account is the address on the page. A different address is not spent. A mainnet account is refused. The thin bar lists tKAS, POCencept, and KUSDT. The bank card opens when you click a clerk. It is a centered swap popup. Three balance cards show tKAS, POCencept, and KUSDT, with locked and purse on the toy cards. Step 1 locks tKAS. Step 2 redeems toy dollars. The Result line on the panel says whether the swap landed. A lock looks for that Testnet 10 payment on the public transaction list. That list stopped storing new payments on 25 Sep 2026. When the list does not have the payment, the server reads it from a synced node, from about the last minute of accepted blocks. The sender and the reserve output still have to match. The live quote and the reserve address sit on the fine line. Three booths. Each booth says its name once. The open booth is the one whose buttons show. tKAS locks into POCencept or KUSDT at the live quote. POCencept redeems the locked part and can hand out the practice purse. KUSDT is the booth with the freeze. The purse adds 20.00 to POCencept and 20.00 to KUSDT. Those coins are unlocked. A shop burns the purse before the locked part. The purse does not redeem. A failed redeem puts the toy balance back. Redeem sends tKAS back only for the locked portion. Opening the bank, a shop, the rules, the bench, or the guide hides Who pays. The peg note sits in Rules.

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
