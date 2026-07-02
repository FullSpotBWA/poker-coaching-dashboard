# 🃏 Revue des Flashcards — Dashboard Poker

> Liste complète des 66 cartes du `quizData`. Indique-moi les numéros (ex: "5, 12, 23 à revoir") des cartes dont **la question et la réponse ne correspondent pas** ou qui sont **mal formulées**.

---

## SESSION 01 — PKO & ICM (16 cartes Concepts)

### #1
**Q :** En PKO TF, de combien est réduit le Risk Premium par rapport à un tournoi Vanilla ?
**R :** ~⅓ plus faible (environ 33% de réduction)
*Tag : PKO*

### #2
**Q :** Pourquoi y a-t-il moins d'ICM en PKO ?
**R :** Structure "top heavy" : le 1er gagne sa bounty + celle du 2ème. Souvent le double du 2ème ou plus. Plus d'incentive à jouer la win.
*Tag : ICM*

### #3
**Q :** Quelles sont les deux forces opposées en PKO ICM ?
**R :** L'ICM augmente le Risk Premium (jetons perdus > gagnés). Les Bounties le diminuent (gain direct). Ces forces s'opposent et parfois se neutralisent (RP ≈ 1).
*Tag : FONDAMENTAL*

### #4
**Q :** En TF PKO, combien vaut un starting bounty power de 1 ?
**R :** ~45% du stack du joueur adverse
*Tag : CALCUL*

### #5
**Q :** Quand on est chip leader et qu'on couvre un joueur, que se passe-t-il avec le RP ?
**R :** Le RP peut devenir négatif. L'ICM est compensé voire dépassé par la bounty potentielle.
*Tag : STRATÉGIE*

### #6
**Q :** Chip Leader 85bb vs stack 60bb : quel RP en Vanilla vs PKO ?
**R :** Vanilla : ~6% RP. PKO : RP négatif (bounty compense l'ICM)
*Tag : COMPARAISON*

### #7
**Q :** Chip Leader vs les blindes en PKO : quel RP ?
**R :** RP = 1 exactement. On joue parfait chip EV.
*Tag : STRATÉGIE*

### #8
**Q :** En PKO postflop, comment joue le stack couvrant ?
**R :** Bet plus gros, trap moins, threshold de value plus bas. Il veut mettre l'argent au milieu car il gagne un bonus (bounty).
*Tag : POSTFLOP*

### #9
**Q :** En PKO postflop, comment joue le stack couvert ?
**R :** Bluff moins (Villain over-call pour la bounty), mais value thin plus car Villain call trop light.
*Tag : POSTFLOP*

### #10
**Q :** Quel est le threshold de value river en Chip EV ?
**R :** ~78-79% d'équité pour 3-barrel value
*Tag : THRESHOLD*

### #11
**Q :** Comment évolue le threshold de value en PKO ?
**R :** Il baisse proportionnellement au bounty power. Plus la bounty est grosse, moins on a besoin d'équité pour value.
*Tag : THRESHOLD*

### #12
**Q :** OOP avec les nuts en PKO : quelle line ?
**R :** Jam direct au lieu de petit sizing. IP va call beaucoup plus pour la bounty. Maximiser la value.
*Tag : POSTFLOP*

### #13
**Q :** Pourquoi y a-t-il moins de slowplay en PKO ?
**R :** Couvrant ET couvert veulent aller vers le nœud "all-in" (pour la bounty). Moins de checks strong, moins de traps river.
*Tag : STRATÉGIE*

### #14
**Q :** Comment adapter le bluff/value ratio selon le bounty power ?
**R :** Plus la bounty est grosse, plus Villain over-call → réduire les bluffs proportionnellement.
*Tag : RATIO*

### #15
**Q :** En Space KO avec une bounty énorme, comment jouer ?
**R :** RP contre ce joueur = extrêmement bas. Il doit jouer ultra tight, on peut call super wide.
*Tag : SPACE KO*

### #16
**Q :** IP vs Bounty Power élevé : quel sizing au flop ?
**R :** Augmenter les sizings (de 40% à plus gros). OOP va call/raise plus, donc on capitalise avec nos value.
*Tag : SIZING*

---

## SESSION 01 — TAKEAWAYS PKO (6 cartes)

### #17
**Q :** [TAKEAWAY] PKO TF - Réflexe mental sur le RP ?
**R :** Réduire mentalement le RP de ~⅓ vs Vanilla. Jouer plus loose.

### #18
**Q :** [TAKEAWAY] PKO - Quand je couvre un adversaire, mon RP est ?
**R :** Peut être négatif. Élargir ma range vs les stacks que je couvre.

### #19
**Q :** [TAKEAWAY] PKO - Approximation valeur d'élimination en TF ?
**R :** 1 starting bounty ≈ 45% du stack adverse

### #20
**Q :** [TAKEAWAY] PKO postflop couvrant - Règle d'action ?
**R :** Bet bigger, trap moins. Mettre l'argent au milieu avec mes value hands.

### #21
**Q :** [TAKEAWAY] PKO postflop couvert - Règle d'action ?
**R :** Bluff moins, value thin plus. Villain call au-dessus de sa MDF pour ma bounty.

### #22
**Q :** [TAKEAWAY] PKO OOP avec les nuts - Sizing ?
**R :** Jam direct au lieu de petit sizing. IP va call beaucoup plus.

---

## SESSION 02 — SQZ 80bb SB vs HJ (15 cartes Concepts)

### #23
**Q :** Configuration du spot SQZ SB vs HJ : qui a fold ?
**R :** HJ open → CO call → SB squeeze → HJ call → CO fold. On joue OOP vs la range forte de HJ (~80-110 combos).
*Tag : SPOT*

### #24
**Q :** Sur quels boards high cards faut-il range bet après un squeeze ?
**R :** Ace High, King High, Jack High. Notre range de squeeze domine ces textures.
*Tag : TEXTURE*

### #25
**Q :** Pourquoi Queen High est différent des autres high cards après SQZ ?
**R :** Queen High est bon pour le caller PF (QJ, QTs, AQ dans sa range). C'est la texture high card où on check le plus.
*Tag : TEXTURE*

### #26
**Q :** Quelle fréquence de check sur les low boards connectés (7-6-5) après SQZ ?
**R :** ~60-70% de check. IP a tous les sets (44-88), nous aucun. Équités ~50/50.
*Tag : FRÉQUENCE*

### #27
**Q :** Pourquoi on n'a aucun set sur les low boards après un SQZ ?
**R :** On squeeze tight donc on n'a pas 44, 55, 66, 77, 88 dans notre range. IP les a tous.
*Tag : RANGE*

### #28
**Q :** Sur un board à straights (7-6-5) après SQZ, quelle stratégie ?
**R :** Check toute notre range. Puis check-raise overpairs et backdoor flush draws. IP doit stab tous ses airs.
*Tag : STRATÉGIE*

### #29
**Q :** Sur boards pairés bas (4-3-3) après SQZ, quel sizing ?
**R :** Big size polarisé (2/3 pot). Les small bets n'accomplissent rien — IP fold seulement 0-9%.
*Tag : SIZING*

### #30
**Q :** Quelles mains bet sur boards pairés bas après SQZ ?
**R :** JJ+ (overpairs fortes mais vulnérables). Check 88, 77 pour pot control.
*Tag : VALUE*

### #31
**Q :** Sur board pairé, pourquoi bet 50% stack au turn plutôt que shove ?
**R :** Nos bluffs (KT, A9) ont peu d'équité, pas de draws. On veut pouvoir fold river si besoin.
*Tag : TURN*

### #32
**Q :** Quels sont les bons bluffs de check-raise OOP après SQZ ?
**R :** Backdoor flush draws, pas les gutshots secs. Il faut trouver ses backdoors.
*Tag : BLUFF*

### #33
**Q :** Vs HJ plus tight (~80 combos vs ~110), comment ajuster ?
**R :** +3-5% de checks sur les mauvaises textures (low connectés). High cards : rien ne change, toujours range bet.
*Tag : AJUSTEMENT*

### #34
**Q :** Quelles mains disparaissent de la range HJ si il est tight ?
**R :** A5s, A3s, K6s, AJo, KQo — les combos marginaux.
*Tag : RANGE*

### #35
**Q :** IP float vs bet 2/3 sur board pairé : quelles mains ?
**R :** KTs, AJo, QJo — difficile à trouver mais nécessaire.
*Tag : FLOAT*

### #36
**Q :** Exploit vs weak regs sur brick boards après SQZ ?
**R :** Range bet 25% même sur bricks. En théorie IP fold 9%, en pratique ils over-fold K9s, QTs etc.
*Tag : EXPLOIT*

### #37
**Q :** Fréquence de check moyenne sur toutes textures après SQZ SB vs HJ ?
**R :** ~21-25% de check en moyenne.
*Tag : FRÉQUENCE*

---

## SESSION 02 — TAKEAWAYS SQZ (6 cartes)

### #38
**Q :** [TAKEAWAY] SQZ - Action sur boards High Cards (A/K/J) ?
**R :** Range bet sans réfléchir. Notre range domine.

### #39
**Q :** [TAKEAWAY] SQZ - Action sur Queen High ?
**R :** Plus de prudence. QJ, QTs, AQ sont dans la range de call HJ.

### #40
**Q :** [TAKEAWAY] SQZ - Règle sur low boards connectés ?
**R :** Check 60-70%. IP a TOUS les sets, nous AUCUN.

### #41
**Q :** [TAKEAWAY] SQZ - Action sur boards à straights ?
**R :** Check range puis check-raise les overpairs et backdoors.

### #42
**Q :** [TAKEAWAY] SQZ - Brick boards pairés (4-3-3) - Action ?
**R :** Big size polarisé 2/3 pot. JJ+ veut value + protection.

### #43
**Q :** [TAKEAWAY] SQZ - Overpairs moyennes (88, 77) sur paired boards ?
**R :** Pot control, check. Trop vulnérables pour bet/call 3 streets.

---

## SESSION 03 — Exploits ICM en TF (T. Boivin) — 15 cartes Concepts

### #44
**Q :** Quel est le profil de joueur qu'on cherche à exploiter dans ce coaching Boivin ?
**R :** Joueur agressif à notre gauche qui 3-bet trop souvent en TF (manque de balance bluff/value).
*Tag : PROFIL*

### #45
**Q :** Quels combos un joueur agro 3-bet à tort en TF (RP élevé) ?
**R :** A4s, A5s, A7s, A8s, K6s, K7s, K8s, KQo, AJo, parfois A9s — combos qui devraient flat.
*Tag : COMBOS*

### #46
**Q :** Scénario 1 - Middle stack vs CO agressif : que devient notre range d'open ?
**R :** On open ~2% plus wide. Le 3-bet du CO devient une décision profitable avec toute notre range.
*Tag : OPEN*

### #47
**Q :** Pourquoi on open plus wide face à un 3-better trop fréquent ?
**R :** Le 3-bet revient à nous avec toute la range, et la décision (fold/call/4-bet) devient pure et profitable.
*Tag : LOGIQUE*

### #48
**Q :** Scénario 2 - CL avec range wide vs BU agro : double exploit ?
**R :** 1) Réduire range d'open (de 42% à 30%) 2) Une fois open, presque jamais fold face au 3-bet, shove tout (paires, suited, KTo, QTo).
*Tag : DOUBLE*

### #49
**Q :** Pourquoi le CL avec range wide doit-il réduire son open vs BU agro ?
**R :** On ne peut pas 4-bet shove toute la range, donc on est obligé de jouer plus tight pour ne pas fold trop souvent.
*Tag : RANGE-RED*

### #50
**Q :** Scénario 3 - CL avec range tight vs CO agro : adaptation ?
**R :** On ne change pas le % d'open (33%), mais on modifie la composition pour blocker le 3-bet et 4-bet shove.
*Tag : COMPOSITION*

### #51
**Q :** Comment modifier la composition de range pour 4-bet shove plus ?
**R :** Enlever les mains qui foldent (Q5, Q6, Q7, Q9, K9, J9) et ajouter des paires basses (33+) et combos shoveable.
*Tag : DETAIL*

### #52
**Q :** Que sont les A-blockers et K-blockers en open dans ce contexte ?
**R :** On open des mains comme K2s, K8s, J10o, A2o pour blocker la range value du 3-better adverse.
*Tag : BLOCKERS*

### #53
**Q :** Côté IP - Si CO fold trop face au 3-bet, comment exploiter au BU ?
**R :** Augmenter sa fréquence de 3-bet : de 11% à 16% (modeste si BB peut s'adapter), jusqu'à 27% si BB ne s'adapte pas.
*Tag : IP-3BET*

### #54
**Q :** BU vs CO qui under-defend : quelle stratégie de 3-bet ?
**R :** Tout en small 3-bet (pas de reshove), même AQo. Si CO 4-bet, on fold tout car sa range est trop forte.
*Tag : STRATÉGIE*

### #55
**Q :** Inversion des stacks (BU couvre CO) : exploit IP plus agressif ?
**R :** BU peut passer de 12% à 35% de 3-bet (presque triplé) si CO under-defend, voire 40-50% en pratique live.
*Tag : BU-COVER*

### #56
**Q :** Pourquoi le RP asymétrique permet d'étendre la range BU rapidement ?
**R :** BU a un RP faible (il couvre), CO a un gros RP. BU peut étendre vite, CO ne peut pas s'adapter sans grosses déviations.
*Tag : ASYMÉTRIE*

### #57
**Q :** Hit ICM dans ce coaching : que veut dire "node lock" ?
**R :** Forcer une déviation dans le solver (ex: réduire fréquence de 3-bet de 6% à 4%) pour calculer notre exploit optimal.
*Tag : SOLVER*

### #58
**Q :** Pourquoi les bluffs en 4-bet shove sont 0 EV à l'équilibre ?
**R :** Par définition, les bluffs sont en général break-even pour balancer la range value. C'est normal.
*Tag : THÉORIE*

---

## SESSION 03 — TAKEAWAYS Exploits ICM (8 cartes)

### #59
**Q :** [TAKEAWAY] Joueur agro à ma gauche qui 3-bet trop : adaptation préflop ?
**R :** J'open un peu plus wide (~+2%) car chaque 3-bet devient une décision profitable.

### #60
**Q :** [TAKEAWAY] Comment identifier un 3-better trop fréquent ?
**R :** Il 3-bet K6s-K8s, A4s-A8s, KQo, AJo automatiquement en TF malgré le RP élevé.

### #61
**Q :** [TAKEAWAY] Si je suis CL avec range wide ET joueur agro à gauche : double action ?
**R :** 1) Tighten mon open 2) Élargir mon 4-bet shove (presque tout shove face au 3-bet).

### #62
**Q :** [TAKEAWAY] Si je suis CL avec range tight ET joueur agro à gauche : action ?
**R :** Garder le % d'open mais blocker-oriented. Je peux ensuite 4-bet shove vraiment large.

### #63
**Q :** [TAKEAWAY] Comment exploiter un PFR qui under-defend face aux 3-bet ?
**R :** Augmenter ma fréquence de 3-bet en IP, surtout en small sizing.

### #64
**Q :** [TAKEAWAY] Si je couvre le PFR et qu'il under-defend : combien de 3-bet ?
**R :** Je peux passer de 12% à 35-50% selon le profil et l'adaptation des blindes.

### #65
**Q :** [TAKEAWAY] Règle d'or face à un node lock ICM : que retenir ?
**R :** Toujours vérifier les hypothèses (qui s'adapte ? qui ne s'adapte pas ?) avant d'exploiter à fond.

### #66
**Q :** [TAKEAWAY] En live vs amateur en TF : peut-on tripler la fréquence de 3-bet ?
**R :** Oui dans les bons spots avec bonnes reads, c'est un game changer. Pas la strat par défaut, mais très profitable.

---

## 📋 Comment me répondre

Indique-moi simplement les numéros à revoir, par exemple :
> "À corriger : #5, #12, #44 (la question parle de profil mais la réponse liste des combos), #48"

Ou :
> "À supprimer complètement : #57, #58"

Je referai ensuite une passe sur chaque carte signalée pour reformuler la Q ou la R afin qu'elles soient cohérentes.
