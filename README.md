> **Experimental only. Not a product.**
>
> Do not use wallet integrations on this GitHub. STP remains a clown. [DISCLAIMER.md](DISCLAIMER.md)

# Why, what, how

One note for the Testnet-10 square at [sixpack.wtf/1984.html](https://sixpack.wtf/1984.html). The page code is [STP-KAS/sixpack.wtf](https://github.com/STP-KAS/sixpack.wtf) at [`1f1b225`](https://github.com/STP-KAS/sixpack.wtf/commit/1f1b225231b53831df27f04ac416d7bce2f2287f). This repository does not run the page.

Read on 29 Sep 2026 against that commit. A local edit on this desk that is not in that commit is not this note.

## Why

The square puts three ways to pay on one counter, so the difference is visible.

**tKAS** is the native Testnet-10 coin. It is the coin that moves. A shop payment is a transaction to the reserve shown on the page. The miner fee is extra tKAS and is outside the price.

**POCencept** is a proof-of-concept stable tag in the village ledger, quoted in toy cents, so a shop can be paid while tKAS stays put. The practice behind the tag is older desk work: grams are prepaid mass, PegLab is the classroom where a thin peg breaks, Ishum quotes a price and settles KAS, and BitCoffee is a Testnet-10 covenant dollar this desk left where it was written. This square did not re-mint those assets.

**KUSDT** is a tether-style tag in the same ledger. It exists so a freeze switch can be seen. Freeze blocks KUSDT only. POCencept and tKAS still pay.

KCC-20 is still Draft. There is no spendable layer-1 stable in this till. The three rails are Testnet-10 toys on proof of work.

## What

1984 is a basic, adjustable toy. A person walks up to a shop on proof of work and pays with one of the three rails. The town on the page is Ashfields. The drawing is original: stone town, dirt path, fountain, stalls, and a roadster that stays on the square. A lap is a turn. Jagex art, the RuneScape wordmark, a private-server engine, a soundtrack file, and the Tidewater fishing island are absent.

The shops are Nia's Cafe, Orin's Table, Mara's Groceries, and Pike's Roadster. Pike sells the roadster for 20.00 toy dollars. After that you drive it on the square. Walk into a shop and you get out. The car does not leave town. Venn's bank is a room with three booths. It opens as a swap popup: a tKAS box, a toy-dollar box, and a Result line on the panel.

A welcome gate comes up first. The top bar shows who is paying and the three balances. Who pays starts closed, in the corner. The left side opens the square, the shops, the bank, the spending rules, the bench, and the guide. The page asks for no seed. A mainnet wallet is refused.

GitHub Pages serves the page. The ledger runs with the sixpack server. The page calls that server for balances, the live KAS price, a test-tab open, and a shop spend.

## How

**New arrival** asks the server for a funded test address that exists only in that browser tab. The browser receives the address and a token. It receives no key. The address and token sit in session storage. They are not written into the saved-wallet store. The fund is 400 tKAS. Close the tab and the leftover is swept back to the reserve after a short grace, so a refresh does not burn the wallet. One network can open 8 of these in a UTC day. The day allows 40 in all. When that allowance is already used, the card closes, the square opens, and the chat says a new test wallet waits until tomorrow. Nothing is minted.

**Returning** closes the gate and leaves Ashfields open. Who pays stays closed. Kasware, Kastle, a pasted `kaspatest:` address, or a `.kas` name that already resolves stays on this browser and keeps its history. A name that points at you ties the public spend to you. A plain address is the preference here. Creating a name is KNS. This page only resolves one.

**Moving.** Click the ground to walk. Hold the left mouse button and move to look all the way around. Left and right turn the view. W A S D move the way you look. Buy the roadster and you drive it on the square. Inside a shop you get out and walk. E talks. Esc closes.

**A shop.** One rail for the whole menu. It opens on POCencept. One Buy button. Prices stay toy cents when the KAS price moves. Coffee is 2.50 toy dollars, supper is 14.00, the roadster is 20.00, and a lap of the square is 100.00. For tKAS, the till converts those cents with the live KAS/USD quote shown on the page. A short payment is refused. The same transaction does not mint the tag twice. POCencept and KUSDT move only in the ledger.

**The bank.** The thin bar lists tKAS, POCencept, and KUSDT. The bank opens as a centered swap popup. Three balance cards show tKAS, POCencept, and KUSDT, with locked and purse on the toy cards. Step 1 locks tKAS. Step 2 redeems toy dollars. The Result line on the panel says whether the swap landed. The live quote and the reserve address sit on the fine line. Three booths. The open booth is the one whose buttons show. tKAS locks into POCencept or KUSDT at the live quote. POCencept redeems the locked part and can hand out the practice purse. KUSDT is the booth with the freeze. The purse adds 20.00 to POCencept and 20.00 to KUSDT. Those coins are unlocked. A shop burns the purse before the locked part. The purse does not redeem. A failed redeem puts the toy balance back. Redeem sends tKAS back only for the locked portion. Opening the bank, a shop, the rules, the bench, or the guide hides Who pays. The peg note sits in Rules.

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
