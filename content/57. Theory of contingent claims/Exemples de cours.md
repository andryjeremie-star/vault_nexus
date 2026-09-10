# Exemples de cours : Theory of Contingent Claims

Ce document rassemble l'ensemble exhaustif des **énoncés et des corrections détaillées des exemples du cours** de *Theory of Contingent Claims* (support officiel CY Tech / M2 MAIF par Erik Taflin et Aktar Yalçin), classés selon les sections du cours.

---

## 1. Marché Monopériode (Section 2)

> [!question] Exemple 2.6 — Couverture d'un Put en marché monopériode (Slides 27-29)
> - **Cadre financier :** Taux sans risque $r = 10\%$, deux actions $S^1$ et $S^2$ de prix initiaux $S^1_0 = S^2_0 = 100$.
> - **Prix à l'échéance $T$ dans l'univers $\Omega = \{\omega_1, \omega_2, \omega_3\}$ (Eq. 11-12) :**
>   - Pour l'action $S^1$ : $S^1_T(\omega_1) = 88, \quad S^1_T(\omega_2) = 110, \quad S^1_T(\omega_3) = 132$
>   - Pour l'action $S^2$ : $S^2_T(\omega_1) = 132, \quad S^2_T(\omega_2) = 88, \quad S^2_T(\omega_3) = 110$
> - **Objectif :** Trouver le [[57.1.23. Portefeuille de couverture|portefeuille de couverture]] $\theta$ d'une [[57.1.6. Option de vente|option de vente (Put)]] sur $S^1$ de strike $K = 105$. Quel est son prix initial $V_0(\theta)$ ?

> [!success] Correction détaillée : Exemple 2.6
> 
> **1. Vecteur de pay-off terminal du Put :**
> Le pay-off est $X = (105 - S^1_T)^+$ :
> - En $\omega_1$ : $X(\omega_1) = (105 - 88)^+ = 17$
> - En $\omega_2$ : $X(\omega_2) = (105 - 110)^+ = 0$
> - En $\omega_3$ : $X(\omega_3) = (105 - 132)^+ = 0$
> 
> En notation matricielle :
> $$X = \begin{pmatrix} 17 \\ 0 \\ 0 \end{pmatrix}$$
> 
> ---
> 
> **2. Système de réplication matriciel (Eq. 13-14) :**
> L'actif sans risque à $t=T$ vaut $S^0_T = (1+r)S^0_0 = 1.10 \times 1 = \frac{11}{10}$.
> La condition de réplication $V_T(\theta) = X$ s'écrit $S \Theta = X$ :
> $$\begin{cases} \frac{11}{10} \theta^0 + 88 \theta^1 + 132 \theta^2 = 17 \\ \frac{11}{10} \theta^0 + 110 \theta^1 + 88 \theta^2 = 0 \\ \frac{11}{10} \theta^0 + 132 \theta^1 + 110 \theta^2 = 0 \end{cases}$$
> 
> ---
> 
> **3. Inversion et portefeuille de couverture (Eq. 15) :**
> En soustrayant la 2e équation à la 3e :
> $$(132 - 110)\theta^1 + (110 - 88)\theta^2 = 0 \implies 22\theta^1 + 22\theta^2 = 0 \implies \theta^2 = -\theta^1$$
> En réinjectant dans la 2e équation :
> $$\frac{11}{10} \theta^0 + (110 - 88)\theta^1 = 0 \implies \frac{11}{10} \theta^0 = -22\theta^1 \implies \theta^0 = -20\theta^1$$
> Dans la 1re équation :
> $$-22\theta^1 + (88 - 132)\theta^1 = 17 \implies -66\theta^1 = 17 \implies \theta^1 = -\frac{17}{66}$$
> On en tire :
> $$\theta^2 = \frac{17}{66}, \quad \theta^0 = -20\left(-\frac{17}{66}\right) = \frac{170}{33}$$
> 
> Le portefeuille de couverture unique est :
> $$\theta = \left( \frac{170}{33}, \; -\frac{17}{66}, \; \frac{17}{66} \right)$$
> 
> Son prix initial à $t=0$ est :
> $$V_0(\theta) = \theta^0 S^0_0 + \theta^1 S^1_0 + \theta^2 S^2_0 = \frac{170}{33}(1) - \frac{17}{66}(100) + \frac{17}{66}(100) = \frac{170}{33} \approx 5.1515$$

---
> [!question] Variante du cours : Intervalle d'AOA pour un taux sans risque $r$ inconnu (Exemple 2.6)
> - **Problématique :** On conserve les mêmes prix terminaux $S^1_T$ et $S^2_T$ sur $\Omega = \{\omega_1, \omega_2, \omega_3\}$, mais le taux d'intérêt sans risque $r$ n'est plus fixé à $10\%$.
> - **Question :** Déterminer l'intervalle exact des valeurs de $r$ garantissant l'absence d'opportunité d'arbitrage (AOA), c'est-à-dire l'existence d'une [[57.1.21. Mesure de martingale équivalente|mesure martingale équivalente]] $\mathbb{Q} = (q_1, q_2, q_3)$ à composantes strictement positives ($q_i > 0$).
> - **Application au Put :** Exprimer le portefeuille de couverture et le prix initial du Put en fonction de $r$.

> [!success] Correction détaillée : Intervalle d'AOA et sensibilité à $r$ (Exemple 2.6)
> 
> **1. Système de martingale sous mesure $\mathbb{Q}$ :**
> L'actif sans risque a pour rendement brut $1+r$. La condition de martingale $\mathbb{E}_\mathbb{Q}[S^i_T] = (1+r)S^i_0$ avec $S^1_0 = S^2_0 = 100$ s'écrit :
> $$\begin{cases} q_1 + q_2 + q_3 = 1 \\ 88 q_1 + 110 q_2 + 132 q_3 = 100(1+r) \\ 132 q_1 + 88 q_2 + 110 q_3 = 100(1+r) \end{cases}$$
> 
> ---
> 
> **2. Résolution analytique en fonction de $r$ :**
> En soustrayant la 2e équation à la 3e :
> $$(132 - 88) q_1 + (88 - 110) q_2 + (110 - 132) q_3 = 0$$
> $$44 q_1 - 22 q_2 - 22 q_3 = 0 \implies 2 q_1 = q_2 + q_3$$
> 
> En injectant $q_2 + q_3 = 2 q_1$ dans la condition de normalisation $q_1 + q_2 + q_3 = 1$ :
> $$q_1 + 2 q_1 = 1 \implies 3 q_1 = 1 \implies q_1 = \frac{1}{3}$$
> *Remarque :* La probabilité de l'état $\omega_1$ est strictement invariante par rapport à $r$ ($q_1 = 1/3$).
> 
> On en déduit :
> $$q_3 = \frac{2}{3} - q_2$$
> 
> En injectant dans la 2e équation :
> $$88\left(\frac{1}{3}\right) + 110 q_2 + 132\left(\frac{2}{3} - q_2\right) = 100(1+r)$$
> $$\frac{88}{3} + 110 q_2 + 88 - 132 q_2 = 100 + 100 r$$
> $$\frac{352}{3} - 22 q_2 = 100 + 100 r \implies 22 q_2 = \frac{352}{3} - 100 - 100 r = \frac{52}{3} - 100 r$$
> En divisant par 22 :
> $$q_2(r) = \frac{52}{66} - \frac{100}{22} r = \frac{26}{33} - \frac{50}{11} r$$
> 
> Puis pour $q_3(r)$ :
> $$q_3(r) = \frac{2}{3} - \left(\frac{26}{33} - \frac{50}{11} r\right) = \frac{22 - 26}{33} + \frac{50}{11} r = -\frac{4}{33} + \frac{50}{11} r$$
> 
> ---
> 
> **3. Conditions de positivité stricte (AOA) :**
> Le marché est sans opportunité d'arbitrage si et seulement si $q_1 > 0$, $q_2 > 0$ et $q_3 > 0$ :
> - $q_1 = \frac{1}{3} > 0$ (toujours vérifié).
> - $q_2(r) > 0 \iff \frac{50}{11} r < \frac{26}{33} \iff r < \frac{26}{33} \times \frac{11}{50} = \frac{26}{150} = \frac{13}{75} \approx 17.33\%$
> - $q_3(r) > 0 \iff \frac{50}{11} r > \frac{4}{33} \iff r > \frac{4}{33} \times \frac{11}{50} = \frac{4}{150} = \frac{2}{75} \approx 2.67\%$
> 
> **Intervalle d'AOA pour $r$ :**
> $$r \in \left] \frac{2}{75}, \; \frac{13}{75} \right[ = \left] \frac{4}{150}, \; \frac{26}{150} \right[ \approx \left] 2.67\%, \; 17.33\% \right[$$
> 
> ---
> 
> **4. Interprétation financière des bornes :**
> - **Si $r \le 2.67\%$ :** Le taux d'intérêt sans risque est trop faible. L'état $\omega_3$ (hausse conjointe des actions) offre un rendement moyen supérieur au cash. Il existe une opportunité d'arbitrage en empruntant du cash pour acheter les actions.
> - **Si $r \ge 17.33\%$ :** Le taux sans risque est trop élevé. Le cash rapporte plus que le portefeuille risqué. Il existe un arbitrage en vendant à découvert les actions pour prêter au taux sans risque.
> - **Pour $r = 10\% = \frac{15}{150}$ :** On est exactement au centre de l'intervalle, où $q_1 = q_2 = q_3 = \frac{1}{3}$ (mesure risque-neutre uniforme).
> 
> ---
> 
> **5. Couverture et prix du Put en fonction de $r$ :**
> Le système de réplication $(1+r)\theta^0 + 88\theta^1 + 132\theta^2 = 17$, etc., donne des positions en actions indépendantes de $r$ :
> $$\theta^1 = -\frac{17}{66}, \quad \theta^2 = \frac{17}{66}$$
> La composante de trésorerie sans risque s'adapte :
> $$(1+r)\theta^0 + (88 - 110)\frac{17}{66} = 0 \implies (1+r)\theta^0 = \frac{17}{3} \implies \theta^0(r) = \frac{17}{3(1+r)}$$
> Le prix initial du Put est :
> $$V_0(\theta) = \theta^0(r) \times 1 + \theta^1(100) + \theta^2(100) = \frac{17}{3(1+r)}$$
> *(Pour $r = 10\%$, on retrouve bien $V_0 = \frac{17}{3 \times 1.1} = \frac{170}{33} \approx 5.1515$).*

---

> [!question] Exemple 2.10 — Évaluation sous E.M.M. et couverture d'un Call (Slides 33-36)
> - **Cadre financier :** Taux sans risque $r = 5\%$, deux actions $S^1, S^2$ et univers à trois états $\Omega = \{\omega_1, \omega_2, \omega_3\}$.
> - **Rendements bruts des actions :**
>   - Pour $S^1$ : $\frac{S^1_T}{S^1_0}(\omega_1) = \frac{42}{31}, \quad \frac{S^1_T}{S^1_0}(\omega_2) = \frac{21}{31}, \quad \frac{S^1_T}{S^1_0}(\omega_3) = \frac{21}{62}$
>   - Pour $S^2$ : $\frac{S^2_T}{S^2_0}(\omega_1) = \frac{21}{124}, \quad \frac{S^2_T}{S^2_0}(\omega_2) = \frac{42}{31}, \quad \frac{S^2_T}{S^2_0}(\omega_3) = \frac{168}{31}$
> - **Probabilités a priori :** $\mathbb{P}(\omega_1) = 1/8, \; \mathbb{P}(\omega_2) = 3/8, \; \mathbb{P}(\omega_3) = 4/8$.
> - **Questions / Objectif :**
>   1. Quel est le prix à $t=0$ d'un [[57.1.4. Option d'achat européenne|Call]] sur $S^2$ de strike $K = \frac{150}{31}S^2_0$ obtenu par une [[57.1.21. Mesure de martingale équivalente|mesure martingale équivalente]] $Q$ ?
>   2. Trouver le portefeuille de couverture du Call et vérifier que sa valeur initiale coïncide avec le prix d'arbitrage.

> [!success] Correction détaillée : Exemple 2.10
> 
> **1. Détermination de l'unique E.M.M. $Q$ (Eq. 20-22) :**
> Avec $1+r = 1.05 = \frac{21}{20}$, la condition $\mathbb{E}_Q[S_T] = (1+r)S_0$ donne le système sur les rendements :
> $$(R)^t \begin{pmatrix} q_1 \\ q_2 \\ q_3 \end{pmatrix} = (1+r) \begin{pmatrix} 1 \\ 1 \\ 1 \end{pmatrix} \iff \begin{cases} q_1 + q_2 + q_3 = 1 \\ \frac{42}{31} q_1 + \frac{21}{31} q_2 + \frac{21}{62} q_3 = \frac{21}{20} \\ \frac{21}{124} q_1 + \frac{42}{31} q_2 + \frac{168}{31} q_3 = \frac{21}{20} \end{cases}$$
> La solution unique est :
> $$q_1 = \frac{3}{5}, \quad q_2 = \frac{3}{10}, \quad q_3 = \frac{1}{10}$$
> Comme $q_i > 0$ pour tout $i$, $Q$ est une E.M.M. unique (marché complet sans arbitrage).
> 
> ---
> 
> **2. Pay-off terminal et prix du Call (Eq. 23) :**
> Le pay-off est $X = \left(S^2_T - \frac{150}{31}S^2_0\right)^+$ :
> - En $\omega_1$ : $\frac{21}{124} < \frac{150}{31} \implies X(\omega_1) = 0$
> - En $\omega_2$ : $\frac{42}{31} < \frac{150}{31} \implies X(\omega_2) = 0$
> - En $\omega_3$ : $\frac{168}{31} > \frac{150}{31} \implies X(\omega_3) = \frac{168 - 150}{31} S^2_0 = \frac{18}{31} S^2_0$
> 
> Prix à $t=0$ :
> $$\Pi_0(X) = \mathbb{E}_Q\left[ \frac{X}{1+r} \right] = q_3 \frac{X(\omega_3)}{1+r} = \frac{1}{10} \times \frac{\frac{18}{31} S^2_0}{\frac{21}{20}} = \frac{1}{10} \times \frac{20}{21} \times \frac{18}{31} S^2_0 = \frac{12}{217} S^2_0 \approx 0.0553 S^2_0$$
> 
> ---
> 
> **3. Portefeuille de couverture (Eq. 24-25) :**
> La condition $X = S \Theta = R \begin{pmatrix} \theta^0 S^0_0 \\ \theta^1 S^1_0 \\ \theta^2 S^2_0 \end{pmatrix}$ donne :
> $$\begin{pmatrix} \theta^0 S^0_0 \\ \theta^1 S^1_0 \\ \theta^2 S^2_0 \end{pmatrix} = S^2_0 \begin{pmatrix} -\frac{3600}{8897} \\ \frac{12}{41} \\ \frac{48}{287} \end{pmatrix}$$
> La valeur initiale du portefeuille est :
> $$V_0(\theta) = \theta^0 S^0_0 + \theta^1 S^1_0 + \theta^2 S^2_0 = S^2_0 \left( -\frac{3600}{8897} + \frac{12}{41} + \frac{48}{287} \right) = \frac{12}{217} S^2_0 = \Pi_0(X)$$
> Le prix de couverture est rigoureusement identique au prix risque-neutre.

---
> [!question] Variante du cours : Intervalle d'AOA pour un taux sans risque $r$ inconnu (Exemple 2.10)
> - **Problématique :** On conserve les rendements bruts des actions $S^1$ et $S^2$ sur l'univers $\Omega = \{\omega_1, \omega_2, \omega_3\}$, mais le taux sans risque $r$ n'est pas fixé à $5\%$.
> - **Question :** Déterminer l'intervalle exact des valeurs de $r$ garantissant l'absence d'opportunité d'arbitrage (AOA), c'est-à-dire l'existence d'une [[57.1.21. Mesure de martingale équivalente|mesure de martingale équivalente]] $\mathbb{Q} = (q_1, q_2, q_3)$ telle que $q_1 > 0, q_2 > 0, q_3 > 0$.
> - **Application au Call :** Exprimer le prix du Call sur $S^2$ en fonction de $r$.

> [!success] Correction détaillée : Intervalle d'AOA et sensibilité à $r$ (Exemple 2.10)
> 
> **1. Système de martingale sous mesure $\mathbb{Q}$ :**
> L'actif sans risque vérifie $\frac{S^0_T}{S^0_0} = 1+r$. Les équations de martingale sur les rendements bruts s'écrivent :
> $$\begin{cases} q_1 + q_2 + q_3 = 1 \\ \frac{42}{31} q_1 + \frac{21}{31} q_2 + \frac{21}{62} q_3 = 1+r \\ \frac{21}{124} q_1 + \frac{42}{31} q_2 + \frac{168}{31} q_3 = 1+r \end{cases}$$
> 
> ---
> 
> **2. Simplification et résolution analytique :**
> Multiplions la 2e équation par $\frac{62}{21}$ :
> $$\frac{62}{21} \times \frac{42}{31} q_1 + \frac{62}{21} \times \frac{21}{31} q_2 + \frac{62}{21} \times \frac{21}{62} q_3 = \frac{62}{21}(1+r)$$
> $$4 q_1 + 2 q_2 + q_3 = \frac{62}{21}(1+r)$$
> 
> Multiplions la 3e équation par $\frac{124}{21}$ :
> $$\frac{124}{21} \times \frac{21}{124} q_1 + \frac{124}{21} \times \frac{42}{31} q_2 + \frac{124}{21} \times \frac{168}{31} q_3 = \frac{124}{21}(1+r)$$
> $$q_1 + 8 q_2 + 32 q_3 = \frac{124}{21}(1+r)$$
> 
> Comme $q_3 = 1 - q_1 - q_2$, la première relation simplifiée devient :
> $$4 q_1 + 2 q_2 + (1 - q_1 - q_2) = \frac{62}{21}(1+r)$$
> $$3 q_1 + q_2 + 1 = \frac{62}{21} + \frac{62}{21} r \implies q_2 = \frac{41}{21} + \frac{62}{21} r - 3 q_1$$
> 
> En substituant $q_3 = 1 - q_1 - q_2$ dans la deuxième relation simplifiée :
> $$q_1 + 8 q_2 + 32(1 - q_1 - q_2) = \frac{124}{21}(1+r)$$
> $$-31 q_1 - 24 q_2 + 32 = \frac{124}{21}(1+r)$$
> $$31 q_1 + 24 q_2 = 32 - \frac{124}{21} - \frac{124}{21} r = \frac{548}{21} - \frac{124}{21} r$$
> 
> En remplaçant $q_2$ par son expression en fonction de $q_1$ :
> $$31 q_1 + 24\left( \frac{41}{21} + \frac{62}{21} r - 3 q_1 \right) = \frac{548}{21} - \frac{124}{21} r$$
> $$(31 - 72) q_1 + \frac{984}{21} + \frac{1488}{21} r = \frac{548}{21} - \frac{124}{21} r$$
> $$-41 q_1 = \frac{548 - 984}{21} - \frac{1488 + 124}{21} r = -\frac{436}{21} - \frac{1612}{21} r$$
> 
> En divisant par $-41$ (sachant que $41 \times 21 = 861$) :
> $$q_1(r) = \frac{436}{861} + \frac{1612}{861} r$$
> 
> On en déduit $q_2(r)$ :
> $$q_2(r) = \frac{41 \times 41}{861} + \frac{62 \times 41}{861} r - 3\left( \frac{436}{861} + \frac{1612}{861} r \right)$$
> $$q_2(r) = \frac{1681 - 1308}{861} + \frac{2542 - 4836}{861} r = \frac{373}{861} - \frac{2294}{861} r$$
> 
> Et enfin $q_3(r) = 1 - q_1(r) - q_2(r)$ :
> $$q_3(r) = 1 - \frac{436 + 373}{861} - \frac{1612 - 2294}{861} r = \frac{52}{861} + \frac{682}{861} r$$
> 
> *(Vérification : Pour $r = 5\% = \frac{1}{20}$, on a $q_1 = \frac{3}{5}$, $q_2 = \frac{3}{10}$, $q_3 = \frac{1}{10}$, conforme à la diapositive 35).*
> 
> ---
> 
> **3. Conditions de positivité stricte (AOA) :**
> L'existence d'une E.M.M. équivaut à la stricte positivité des trois probabilités :
> - $q_1(r) > 0 \iff 1612 r > -436 \iff r > -\frac{436}{1612} = -\frac{109}{403} \approx -27.05\%$
> - $q_2(r) > 0 \iff 2294 r < 373 \iff r < \frac{373}{2294} \approx 16.26\%$
> - $q_3(r) > 0 \iff 682 r > -52 \iff r > -\frac{52}{682} = -\frac{26}{341} \approx -7.62\%$
> 
> En prenant l'intersection des trois conditions :
> $$-\frac{26}{341} < r < \frac{373}{2294}$$
> 
> **Intervalle d'AOA pour $r$ :**
> $$r \in \left] -\frac{26}{341}, \; \frac{373}{2294} \right[ \approx \left] -7.62\%, \; 16.26\% \right[$$
> *(Sous l'hypothèse économique usuelle d'un taux nominal sans risque positif $r \ge 0$, l'intervalle admissible est $\left[ 0, \; \frac{373}{2294} \right[ \approx [0\%, 16.26\%[$).*
> 
> ---
> 
> **4. Interprétation financière :**
> - Si $r \ge \frac{373}{2294} \approx 16.26\%$, $q_2 \le 0$ : le rendement du cash sans risque surpasse le rendement moyen pondéré des actions. Une opportunité d'arbitrage s'ouvre en vendant à découvert les actions pour prêter au taux sans risque.
> - Si $r \le -\frac{26}{341} \approx -7.62\%$, $q_3 \le 0$ : le coût du cash est trop faible, ce qui engendre un arbitrage en empruntant du cash pour sur-pondérer l'action $S^2$ qui explose en $\omega_3$.
> 
> ---
> 
> **5. Prix du Call en fonction de $r$ :**
> Le pay-off étant $X(\omega_3) = \frac{18}{31} S^2_0$ et 0 ailleurs, le prix d'arbitrage s'écrit directement :
> $$\Pi_0(X)(r) = \mathbb{E}_\mathbb{Q}\left[ \frac{X}{1+r} \right] = \frac{q_3(r)}{1+r} \times \frac{18}{31} S^2_0 = \frac{\frac{52}{861} + \frac{682}{861} r}{1+r} \times \frac{18}{31} S^2_0$$
> *(Pour $r = 5\% = \frac{1}{20}$, on retrouve bien $\Pi_0(X) = \frac{12}{217} S^2_0 \approx 0.0553 S^2_0$).*

---

## 2. Marchés en Temps Discret & Modèle Binomial (Section 3)

> [!question] Exemple 3.1 — Filtration et arbre d'information ($T = 3$) (Slides 47-50)
> - **Cadre :** Modèle à $T = 3$ périodes sur $\Omega = \{\omega_0, \dots, \omega_7\}$ ($\bar{K} = 2^3 = 8$ états).
> - **Questions / Objectif :**
>   1. Expliciter les partitions successives générant la [[57.2.1. Modèle probabiliste en temps discret Filtered Probability Space|filtration]] $\mathcal{F}_0 \subset \mathcal{F}_1 \subset \mathcal{F}_2 \subset \mathcal{F}_3$.
>   2. Caractériser la condition de mesurabilité d'une variable aléatoire $X$ à chaque date $t$.

> [!success] Correction détaillée : Exemple 3.1
> 
> **1. Partitions et filtration (Slides 48-49, Eq. 28) :**
> Selon la convention binaire où $\omega_k$ a pour coordonnées les bits de l'entier $k$ ($0$ pour baisse $d$, $1$ pour hausse $u$) :
> - $\mathcal{F}_0 = \{\Omega, \emptyset\}$ (1 atome : $\Omega$).
> - $\mathcal{F}_1 = \sigma(A_1(0), A_1(1))$ avec 2 atomes :
>   $$A_1(0) = \{\omega_0, \omega_1, \omega_2, \omega_3\}, \quad A_1(1) = \{\omega_4, \omega_5, \omega_6, \omega_7\}$$
> - $\mathcal{F}_2 = \sigma(A_2(0,0), A_2(0,1), A_2(1,0), A_2(1,1))$ avec 4 atomes :
>   $$A_2(0,0) = \{\omega_0, \omega_1\}, \quad A_2(0,1) = \{\omega_2, \omega_3\}$$
>   $$A_2(1,0) = \{\omega_4, \omega_5\}, \quad A_2(1,1) = \{\omega_6, \omega_7\}$$
> - $\mathcal{F}_3 = \mathcal{P}(\Omega)$ (8 atomes, singletons $\{\omega_k\}$).
> 
> ---
> 
> **2. Mesurabilité de $X$ (Slide 50) :**
> - $X$ est $\mathcal{F}_0$-mesurable $\iff$ $X$ est constante sur $\Omega$.
> - $X$ est $\mathcal{F}_1$-mesurable $\iff$ $X$ est constante sur $A_1(0)$ et sur $A_1(1)$.
> - $X$ est $\mathcal{F}_2$-mesurable $\iff$ $X$ est constante sur chacun des 4 atomes $A_2(i, j)$.
> - $X$ est $\mathcal{F}_3$-mesurable $\iff$ $X$ est quelconque.

---

> [!question] Exemple 3.2 — Trajectoires de prix dans le modèle binomial (Slides 53-54)
> - **Paramètres :** $U = 2, D = 1/2, p = 3/4, S^1_0 = 1, T = 3$.
> - **Questions / Objectif :**
>   1. Construire l'arbre recombinant des prix de l'actif risqué $S^1$.
>   2. Calculer les probabilités des trajectoires et la loi de probabilité de $S^1_3$.

> [!success] Correction détaillée : Exemple 3.2
> 
> **1. Nœuds de l'arbre recombinant (Slide 53) :**
> - $t = 0$ : $S_0 = 1$
> - $t = 1$ : $S_1 \in \{2, \; 1/2\}$
> - $t = 2$ : $S_2 \in \{4, \; 1, \; 1/4\}$
> - $t = 3$ : $S_3 \in \{8, \; 2, \; 1/2, \; 1/8\}$
> 
> ---
> 
> **2. Probabilités élémentaires et distribution terminale (Slide 54) :**
> Les probabilités des trajectoires vérifient $\mathbb{P}(\omega) = p^n (1-p)^{3-n}$ avec $p = 3/4$ et $1-p = 1/4$ :
> - $\mathbb{P}(\omega_4) = \mathbb{P}(\omega_2) = \mathbb{P}(\omega_1) = p(1-p)^2 = \frac{3}{4} \left(\frac{1}{4}\right)^2 = \frac{3}{64}$
> - $\mathbb{P}(\omega_0) = (1-p)^3 = \left(\frac{1}{4}\right)^3 = \frac{1}{64}$
> 
> Pour le niveau de prix $S^1_3 = 1/2$, trois trajectoires mènent à ce nœud ($\{\omega_1, \omega_2, \omega_4\}$) :
> $$\mathbb{P}(S^1_3 = 1/2) = \mathbb{P}(\{\omega_1, \omega_2, \omega_4\}) = 3 \times \frac{3}{64} = \frac{9}{64}$$
> De même, $\mathbb{P}(S^1_3 = 8) = (3/4)^3 = \frac{27}{64}$ et $\mathbb{P}(S^1_3 = 2) = 3(3/4)^2(1/4) = \frac{27}{64}$.

---

> [!question] Exemple 3.5 — Portefeuille Buy-and-Hold (Slide 58)
> - **Énoncé :** Démontrer qu'un portefeuille Buy-and-Hold $\theta_t = \theta_0, \forall t \in \mathbb{T}$ est [[57.2.15. Portefeuille auto - financé - Self - financing Portfolio Définition 33|auto-financé]].

> [!success] Correction détaillée : Exemple 3.5
> 
> D'après la Proposition 3.4 (Slide 57), une stratégie est auto-financée si et seulement si :
> $$\theta_{t-1} \cdot S_t = \theta_t \cdot S_t, \quad \forall t \in \{1, \dots, T\}$$
> Pour un portefeuille Buy-and-Hold, $\theta_t = \theta_0$ pour tout $t$. On a donc :
> $$\theta_{t-1} \cdot S_t = \theta_0 \cdot S_t = \theta_t \cdot S_t$$
> L'égalité est trivialement vérifiée à chaque date $t$, ce qui prouve formellement l'autofinancement.

---

> [!question] Question d'application — Évaluation d'un Call Européen At-the-Money ($T=3$) (Slides 59-60)
> - **Paramètres :** $T = 3, U = 2, D = 1/2, r = 0, p = 3/4, S^1_0 = 1$.
> - **Contrat :** Call européen de strike $K = 1$ à maturité $T = 3$. Pay-off $X = (S^1_3 - 1)^+$.
> - **Question :** Quel est le prix du Call à $t = 0$ ?

> [!success] Correction détaillée : Question d'application
> 
> **1. Pay-offs terminaux (Slide 59) :**
> - $X(\{\omega_7\}) = (8 - 1)^+ = 7$
> - $X(\{\omega_3\}) = X(\{\omega_5\}) = X(\{\omega_6\}) = (2 - 1)^+ = 1$
> - $X(\{\omega_1\}) = X(\{\omega_2\}) = X(\{\omega_4\}) = (0.5 - 1)^+ = 0$
> - $X(\{\omega_0\}) = (0.125 - 1)^+ = 0$
> 
> ---
> 
> **2. Probabilité risque-neutre et prix d'arbitrage (Slide 60, Eq. 35-36) :**
> $$q = \frac{1+r-D}{U-D} = \frac{1 - 1/2}{2 - 1/2} = \frac{1}{3}$$
> Avec $r = 0$, le prix d'arbitrage est l'espérance sous $Q$ :
> $$\Pi_0(X) = Q(S^1_3 = 2) \times 1 + Q(S^1_3 = 8) \times 7 = 3q^2(1-q) \times 1 + 7q^3$$
> $$\Pi_0(X) = 3\left(\frac{1}{3}\right)^2\left(\frac{2}{3}\right) + 7\left(\frac{1}{3}\right)^3 = \frac{6}{27} + \frac{7}{27} = \frac{13}{27} \approx 0.4815$$

---

> [!question] Exemple 3.13 — Condition d'existence de l'E.M.M. Binomiale (Slide 68)
> - **Énoncé :** Démontrer que pour le marché binomial, il existe une E.M.M. si et seulement si $D < 1+r < U$ ou $D = 1+r = U$.

> [!success] Correction détaillée : Exemple 3.13
> 
> Par la propriété de martingale sous $Q$ :
> $$\frac{S^1_t}{(1+r)^t} = \mathbb{E}_Q\left[ \frac{S^1_{t+1}}{(1+r)^{t+1}} \;\middle|\; \mathcal{F}_t \right] \iff S^1_t = q_t \frac{S^1_t U}{1+r} + (1-q_t) \frac{S^1_t D}{1+r}$$
> En simplifiant par $S^1_t > 0$ :
> $$1+r = q_t U + (1-q_t) D \iff q_t = q \equiv \frac{1+r-D}{U-D}$$
> Pour que $Q$ soit équivalente à $\mathbb{P}$, il faut $0 < q < 1$ :
> - $q > 0 \iff 1+r - D > 0 \iff 1+r > D$
> - $q < 1 \iff 1+r - D < U - D \iff 1+r < U$
> D'où la condition nécessaire et suffisante :
> $$D < 1+r < U \quad (\text{ou } D = 1+r = U \text{ dans le cas dégénéré sans risque})$$

---

> [!question] Exemple 3.15 — Marché de Black-Scholes en temps discret (Slide 69)
> - **Énoncé :** Rappeler le principe de discrétisation de Black-Scholes par le modèle binomial de Cox-Ross-Rubinstein.

> [!success] Correction détaillée : Exemple 3.15
> 
> Sur une subdivision de pas $\Delta t = T/N$, on pose $U = e^{\sigma\sqrt{\Delta t}}, D = e^{-\sigma\sqrt{\Delta t}}$ et $1+r_{\Delta t} = e^{r\Delta t}$.
> La probabilité risque-neutre vaut $q = \frac{e^{r\Delta t} - e^{-\sigma\sqrt{\Delta t}}}{e^{\sigma\sqrt{\Delta t}} - e^{-\sigma\sqrt{\Delta t}}}$.
> Par le théorème central limite, lorsque $N \to +\infty$, la distribution binomiale du log-rendement converge en loi vers la distribution normale continue $\mathcal{N}((r - \sigma^2/2)T, \sigma^2 T)$, et le prix discret converge vers la formule de Black-Scholes.

---

> [!question] Exemple 3.21 — Évaluation multinœud d'un Call Européen (Slide 79)
> - **Énoncé :** Calculer par rétro-propagation les prix $\Pi_t(X)$ et pay-offs pour tous les nœuds de l'arbre binomial $T = 3$ avec $U = 2, D = 1/2, r = 0, K = 1, S^1_0 = 1$.

> [!success] Correction détaillée : Exemple 3.21
> 
> En appliquant récursivement $\Pi_t(X) = q \Pi_{t+1}(u) + (1-q) \Pi_{t+1}(d)$ avec $q = 1/3$ et $1-q = 2/3$ :
> - **À $t = 3$ :**
>   - $X(\{\omega_7\}) = 7$
>   - $X(\{\omega_3, \omega_5, \omega_6\}) = 1$
>   - $X(\{\omega_1, \omega_2, \omega_4\}) = 0$
>   - $X(\{\omega_0\}) = 0$
> - **À $t = 2$ :**
>   - Nœud haut ($S=4$) : $\Pi_2 = \frac{1}{3}(7) + \frac{2}{3}(1) = 3$
>   - Nœud milieu ($S=1$) : $\Pi_2 = \frac{1}{3}(1) + \frac{2}{3}(0) = \frac{1}{3}$
>   - Nœud bas ($S=1/4$) : $\Pi_2 = 0$
> - **À $t = 1$ :**
>   - Nœud haut ($S=2$) : $\Pi_1 = \frac{1}{3}(3) + \frac{2}{3}\left(\frac{1}{3}\right) = \frac{11}{9}$
>   - Nœud bas ($S=1/2$) : $\Pi_1 = \frac{1}{3}\left(\frac{1}{3}\right) + \frac{2}{3}(0) = \frac{1}{9}$
> - **À $t = 0$ :**
>   $$\Pi_0 = \frac{1}{3}\left(\frac{11}{9}\right) + \frac{2}{3}\left(\frac{1}{9}\right) = \frac{13}{27}$$
> Ce sont exactement les valeurs figurant sur le graphe de la Slide 79.

---

> [!question] Exemple 3.22 — Option Barrière (Down-And-Out Call) (Slides 80-83)
> - **Paramètres :** $T = 3, r = 1/10, U = 5/4, D = 4/5, S^1_0 = 400, p = 3/4$.
> - **Contrat :** Down-And-Out Call de barrière $H = 350$ et strike $K = 450$.
>   Pay-off : $X = (S^1_T - K)^+ \mathbb{1}_{\{\min_{0 \le t \le T} S^1_t \ge H\}}$ (Eq. 50-51).
> - **Objectif :** Trouver le prix $\Pi_0(X)$ à $t = 0$.

> [!success] Correction détaillée : Exemple 3.22
> 
> **1. Probabilité risque-neutre (Slide 81) :**
> $$q = \frac{\frac{11}{10} - \frac{4}{5}}{\frac{5}{4} - \frac{4}{5}} = \frac{\frac{3}{10}}{\frac{9}{20}} = \frac{2}{3}$$
> 
> ---
> 
> **2. Trajectoires et pay-offs (Slide 82) :**
> Barrière $H = 350$. Si $S_t < 350$, l'option est désactivée ($X = 0$).
> Les 4 trajectoires commençant par une baisse ont $S_1 = 400 \times 0.8 = 320 < 350$, donc $X(\omega_0) = X(\omega_1) = X(\omega_2) = X(\omega_3) = 0$.
> Pour la trajectoire $UDD$ ($\{\omega_4\}$), $S_3 = 320 < 350$, donc $X(\omega_4) = 0$.
> Seules 3 trajectoires ont un pay-off non nul :
> - $\omega_5$ ($UDU$, $S_3 = 500$) : $X(\omega_5) = (500 - 450)^+ = 50$
> - $\omega_6$ ($UUD$, $S_3 = 500$) : $X(\omega_6) = (500 - 450)^+ = 50$
> - $\omega_7$ ($UUU$, $S_3 = 781.25 = 3125/4$) : $X(\omega_7) = \frac{3125}{4} - 450 = \frac{1325}{4}$
> 
> ---
> 
> **3. Calcul du prix initial (Slide 83) :**
> $$\Pi_0(X) = \frac{1}{(1+r)^T} \mathbb{E}_Q[X] = \left(\frac{10}{11}\right)^3 \left[ 2 \cdot 50 q^2(1-q) + \frac{1325}{4} q^3 \right]$$
> $$\Pi_0(X) = \left(\frac{10}{11}\right)^3 \left[ 100 \left(\frac{2}{3}\right)^2 \left(\frac{1}{3}\right) + \frac{1325}{4} \left(\frac{2}{3}\right)^3 \right] = \left(\frac{10}{33}\right)^3 (400 + 2 \cdot 1325) \approx 84.87$$

---

> [!question] Exemple 3.23 — Option Asiatique (Asian Call Option) (Slides 84-89)
> - **Paramètres :** $T = 4, r = 1/4, D = 1, U = 2, S^1_0 = 10, p = 3/4$.
> - **Contrat :** Option asiatique de strike $K = 35$, pay-off $X = \left(\frac{1}{4}\sum_{t=1}^4 S^1_t - 35\right)^+$ (Eq. 52).
> - **Objectif :** Trouver le prix $(\Pi_X(t))(\omega)$ pour tout $t$ et tout $\omega$.

> [!success] Correction détaillée : Exemple 3.23
> 
> **1. Probabilité risque-neutre et relation de récurrence (Slide 89) :**
> $$q = \frac{\frac{5}{4} - 1}{2 - 1} = \frac{1}{4}$$
> Rétro-propagation :
> $$\Pi_t(X) = \frac{1}{1+r} \mathbb{E}_Q[\Pi_{t+1}(X) \mid \mathcal{F}_t] = \frac{4}{5} \left( \frac{1}{4} \Pi_{t+1}(\text{up}) + \frac{3}{4} \Pi_{t+1}(\text{down}) \right) = \frac{1}{5}\Pi_{t+1}(\text{up}) + \frac{3}{5}\Pi_{t+1}(\text{down})$$
> 
> ---
> 
> **2. Arbre complet des prix à chaque date (Slide 89) :**
> - **À $t = 4$ (Pay-offs finaux de la Slide 88) :**
>   - $X(\omega_{15}) = 40$
>   - $X(\omega_{14}) = 20$
>   - $X(\omega_{13}) = 10$
>   - $X(\omega_{11}) = 5$
>   - $X(\omega_7) = 5/2 = 2.5$
>   - Tous les autres $X(\omega_i) = 0$.
> - **À $t = 3$ :**
>   - $\Pi_3 = \frac{1}{5}(40) + \frac{3}{5}(20) = 8 + 12 = 20$
>   - $\Pi_3 = \frac{1}{5}(10) + \frac{3}{5}(0) = 2$
>   - $\Pi_3 = \frac{1}{5}(5) + \frac{3}{5}(0) = 1$
>   - $\Pi_3 = \frac{1}{5}(5/2) + \frac{3}{5}(0) = 1/2$
>   - Autres nœuds : $0$.
> - **À $t = 2$ :**
>   - $\Pi_2 = \frac{1}{5}(20) + \frac{3}{5}(2) = \frac{26}{5}$
>   - $\Pi_2 = \frac{1}{5}(1) + \frac{3}{5}(0) = \frac{1}{5}$
>   - $\Pi_2 = \frac{1}{5}(1/2) + \frac{3}{5}(0) = \frac{1}{10}$
>   - Dernier nœud : $0$.
> - **À $t = 1$ :**
>   - $\Pi_1(\text{up}) = \frac{1}{5}\left(\frac{26}{5}\right) + \frac{3}{5}\left(\frac{1}{5}\right) = \frac{29}{25}$
>   - $\Pi_1(\text{down}) = \frac{1}{5}\left(\frac{1}{10}\right) + \frac{3}{5}(0) = \frac{1}{50}$
> - **À $t = 0$ :**
>   $$\Pi_0(X) = \frac{1}{5}\left(\frac{29}{25}\right) + \frac{3}{5}\left(\frac{1}{50}\right) = \frac{29}{125} + \frac{3}{250} = \frac{58 + 3}{250} = \frac{61}{250} = 0.244$$

---

> [!question] Exemple 3.24 — Dérivés Américains (Slide 90)
> - **Énoncé :** Définir le pay-off d'un Call américain et d'un Put américain de strike $K$ et maturité $T$ sur un actif $Y$.

> [!success] Correction détaillée : Exemple 3.24
> 
> Pour tout instant d'exercice $t \in \{0, \dots, T\}$ :
> - Call américain : $X_t = (Y_t - K)^+$
> - Put américain : $X_t = (K - Y_t)^+$
> La valorisation par programmation dynamique s'effectue via l'enveloppe de Snell (Slides 91-92, Eq. 54) :
> $$\Pi^{(a)}_t(X) = \max \left( X_t, \; S^0_t \mathbb{E}_Q\left[ \frac{\Pi^{(a)}_{t+1}(X)}{S^0_{t+1}} \;\middle|\; \mathcal{F}_t \right] \right)$$

---

> [!question] Exemple 3.27 — Exercice optimal sous martingale (Slide 94)
> - **Énoncé :** Montrer que si le processus actualisé $X_t / S^0_t$ est une $Q$-martingale, alors $\Pi^{(a)}_t(X) = X_t$ pour tout $t$ et toute suite de temps d'arrêt est optimale.

> [!success] Correction détaillée : Exemple 3.27
> 
> Par le théorème d'arrêt optionnel de Doob, pour tout temps d'arrêt $\tau \in \mathcal{T}_{t, T}$ :
> $$\mathbb{E}_Q\left[ \frac{X_\tau}{S^0_\tau} \;\middle|\; \mathcal{F}_t \right] = \frac{X_t}{S^0_t}$$
> D'après la formule de valorisation américaine (Slide 93, Eq. 55) :
> $$\Pi^{(a)}_t(X) = S^0_t \max_{\tau \in \mathcal{T}_{t, T}} \mathbb{E}_Q\left[ \frac{X_\tau}{S^0_\tau} \;\middle|\; \mathcal{F}_t \right] = S^0_t \left( \frac{X_t}{S^0_t} \right) = X_t$$
> Le dérivé vaut son pay-off immédiat et n'importe quel temps d'arrêt $\tau$ réalise le maximum.

---

> [!question] Exemple 3.28 — Put Américain dans le modèle binomial ($T=1$) (Slide 95)
> - **Paramètres :** Put américain de strike $K = 3/2$ dans le modèle binomial avec $S^1_0 = 1, T = 1, D = 1/2, U = 2$ et $D < 1+r < U$.
> - **Question :** Pour quelles valeurs de $r$ l'exercice anticipé en $t = 0$ est-il optimal ?

> [!success] Correction détaillée : Exemple 3.28
> 
> - Pay-off en $t = 0$ : $X_0 = (3/2 - 1)^+ = 1/2$.
> - Pay-offs en $t = 1$ : $X_1(U) = (3/2 - 2)^+ = 0$ et $X_1(D) = (3/2 - 1/2)^+ = 1$.
> - Probabilité risque-neutre : $q = \frac{1+r-1/2}{2-1/2} = \frac{2r+1}{3} \implies 1-q = \frac{2(1-r)}{3}$.
> - Valeur de continuation à $t = 0$ :
>   $$V_{\text{cont}} = \frac{1}{1+r}\mathbb{E}_Q[X_1] = \frac{1-q}{1+r} = \frac{2(1-r)}{3(1+r)}$$
> - Condition d'optimalité de l'exercice immédiat en $t = 0$ :
>   $$X_0 \ge V_{\text{cont}} \iff \frac{1}{2} \ge \frac{2(1-r)}{3(1+r)} \iff 3(1+r) \ge 4(1-r) \iff 7r \ge 1 \iff r \ge \frac{1}{7}$$
> Conclusion :
> - Si $r > 1/7$ : l'exercice immédiat en $t=0$ est l'unique stratégie optimale ($\hat{\tau}_0 = 0$).
> - Si $r = 1/7$ : les deux stratégies ($t=0$ et $t=1$) sont équivalentes.
> - Si $r < 1/7$ : il est optimal d'attendre l'échéance $t=1$ ($\hat{\tau}_0 = 1$).

---

## 3. Marchés en Temps Continu & Modèle de Black-Scholes (Section 4)

> [!question] Exemple 4.4 — Tarification Black-Scholes d'un Call et d'un Put (Slide 115)
> - **Données du marché :** Taux $r = 3.5\%$, volatilité $\sigma = 30\%$, prix spot $S_t = 132\text{ €}$, échéance $\tau = 9\text{ mois} = 0.75\text{ an}$, strike $K = 125\text{ €}$.
> - **Question :** Quels sont aujourd'hui les prix d'un Call et d'un Put ?

> [!success] Correction détaillée : Exemple 4.4
> 
> Selon les formules (81) et (82) de la Slide 111 :
> $$d_1(\tau) = \frac{1}{\frac{3}{10}\sqrt{3/4}} \left( \ln(132/125) + \frac{3}{4}\left(\frac{35}{1000} + \frac{(3/10)^2}{2}\right) \right) \approx 0.440665$$
> $$d_2(\tau) = \frac{1}{\frac{3}{10}\sqrt{3/4}} \left( \ln(132/125) + \frac{3}{4}\left(\frac{35}{1000} - \frac{(3/10)^2}{2}\right) \right) \approx 0.180858$$
> 
> Valeurs gaussiennes :
> $$N(d_1) \approx 0.670272, \quad N(d_2) \approx 0.571760$$
> 
> Formule du Call (Eq. 83) :
> $$C(t, 132) = 132 \times 0.670272 - 125 e^{-0.035 \times 0.75} \times 0.571760 \approx 18.8576\text{ €}$$
> 
> Par la relation de parité Call-Put (Slide 114, Eq. 85) :
> $$P(t, 132) = C(t, 132) - 132 + 125 e^{-0.035 \times 0.75} \approx 8.61903\text{ €}$$

---

> [!question] Exemple 4.5 — Couverture du Call et du Put de l'Exemple 4.4 (Slide 119)
> - **Question :** Dans la situation de l'Exemple 4.4, quels sont aujourd'hui les portefeuilles de couverture du Call et du Put ?

> [!success] Correction détaillée : Exemple 4.5
> 
> D'après la formule générale (76) et (88) avec $x = 132\text{ €}$ :
> - **Pour le Call :**
>   $$\theta^1_t = N(d_1) \approx 0.670272\text{ actions}$$
>   $$\theta^0_t S^0_t = C(t, x) - N(d_1)x \approx 18.8576 - (0.670272 \times 132) \approx -69.6184\text{ €}$$
>   *(On détient $0.670272$ action et on emprunte $69.6184\text{ €}$).*
> - **Pour le Put :**
>   $$\theta^1_t = N(d_1) - 1 \approx -0.329728\text{ actions}$$
>   $$\theta^0_t S^0_t = P(t, x) - \theta^1_t x \approx 8.61903 - (-0.329728 \times 132) \approx +52.1431\text{ €}$$
>   *(On vend à découvert $0.329728$ action et on prête $52.1431\text{ €}$ au taux sans risque).*

---

> [!question] Exemple 4.6 — Sensibilités et Grecques d'un Put Européen (Slide 119)
> - **Énoncé :** Donner les formules des grecques pour une option de vente européenne (Put).

> [!success] Correction détaillée : Exemple 4.6
> 
> Par dérivation directe de la formule de parité Call-Put $C - P = S - K e^{-r\tau}$ et des formules du Call (Slides 117-118) :
> - **Delta :** $\Delta_P = \frac{\partial P}{\partial S} = \Delta_C - 1 = N(d_1) - 1 = -N(-d_1) < 0$
> - **Gamma :** $\Gamma_P = \frac{\partial^2 P}{\partial S^2} = \Gamma_C = \frac{N'(d_1)}{S \sigma \sqrt{\tau}} > 0$
> - **Theta :** $\Theta_P = \frac{\partial P}{\partial t} = -\frac{S \sigma N'(d_1)}{2\sqrt{\tau}} + r K e^{-r\tau} N(-d_2)$
> - **Vega :** $\mathcal{V}_P = \frac{\partial P}{\partial \sigma} = \mathcal{V}_C = S \sqrt{\tau} N'(d_1) > 0$
> - **Rho :** $\rho_P = \frac{\partial P}{\partial r} = -K \tau e^{-r\tau} N(-d_2) < 0$

---

> [!question] Exemple : Volatilité Stochastique Simple et Smile de Volatilité (Slides 137-138)
> - **Cadre :** $S^1_0 = S^2_0 = 1, r = 0, T = 1$. Volatilité $a_t = 1$ sur $[0, 1/2]$, puis :
>   $a_t = 1/2$ si $S^2_{1/2} \le e^{-1/4}$ et $a_t = 2$ si $S^2_{1/2} > e^{-1/4}$.
> - **Questions / Objectif :**
>   1. Exprimer le prix $p(K)$ du Call en fonction des prix de Black-Scholes à variance intégrée fixée.
>   2. Expliquer l'apparition du smile de volatilité.

> [!success] Correction détaillée : Exemple Volatilité Stochastique Simple
> 
> **1. Calcul de la variance intégrée et prix du Call :**
> Comme $S^2_{1/2} = \exp(W^2_{1/2} - 1/4)$, la condition $S^2_{1/2} > e^{-1/4}$ équivaut à $W^2_{1/2} > 0$, événement de probabilité $1/2$.
> La variance intégrée $\Upsilon = \int_0^1 a_t^2 dt$ prend donc deux valeurs équiprobables :
> - Si $a = 1/2$ : $\Upsilon_1 = \frac{1}{2}(1)^2 + \frac{1}{2}\left(\frac{1}{2}\right)^2 = \frac{1}{2} + \frac{1}{8} = \frac{5}{8}$
> - Si $a = 2$ : $\Upsilon_2 = \frac{1}{2}(1)^2 + \frac{1}{2}(2)^2 = \frac{1}{2} + 2 = \frac{5}{2}$
> 
> Le prix du Call est la moyenne exacte de deux formules de Black-Scholes (Slide 137) :
> $$p(K) = \frac{1}{2} \left( c_{BS}(K, 5/8) + c_{BS}(K, 5/2) \right)$$
> 
> ---
> 
> **2. Apparition du smile :**
> La volatilité implicite $\sigma_{impl}(K)$ est définie par $p(K) = c_{BS}(K, (\sigma_{impl}(K))^2)$.
> En raison de la stricte convexité de la fonction de Black-Scholes par rapport à la volatilité, la moyenne de deux prix de Black-Scholes excède le prix calculé à la volatilité moyenne. L'inversion produit une courbe convexe en fonction du strike $K \mapsto \sigma_{impl}(K)$ présentant un creux et des ailes relevées (**smile de volatilité**, Slide 138).

---

> [!question] Exemple 4.12 — Toy Derivative et Smile dans le Modèle de Heston (Slides 142-143)
> - **Pay-off :** $X_T = \int_0^T \left(\frac{1}{S^1_t}\right)^2 d\langle S^1, S^1 \rangle_t = \Upsilon_T$.
> - **Objectif :** Calculer le prix $P(0, T)$ et la volatilité implicite associée $\sigma_{imp}(T)$.

> [!success] Correction détaillée : Exemple 4.12
> 
> Selon la formule (134) de la Slide 141, sous la dynamique CIR de la variance ($dv_t = k(a - v_t)dt + \delta\sqrt{v_t}d\bar{z}_t$) avec $\lambda = 0$ :
> $$\mathbb{E}_Q[\Upsilon_T] = aT + (v_0 - a) \frac{1 - e^{-kT}}{k}$$
> Le prix du produit dérivé à $t = 0$ vaut (Eq. 136) :
> $$P(0, T) = \mathbb{E}_Q[e^{-rT} \Upsilon_T] = e^{-rT} \left( aT + (v_0 - a) \frac{1 - e^{-kT}}{k} \right)$$
> 
> Par identification avec le prix Black-Scholes $P_{BS}(0, T, \sigma) = e^{-rT}\sigma^2 T$ (Eq. 137-138) :
> $$(\sigma_{imp}(T))^2 = a + (v_0 - a) \frac{1 - e^{-kT}}{kT} \quad (\text{Eq. 139})$$
> La courbe $T \mapsto \sigma_{imp}(T)$ décroît de $\sqrt{v_0}$ (pour $T \to 0$) vers $\sqrt{a}$ (pour $T \to \infty$), traçant le smile de maturité illustré sur la Slide 143 (avec $a = 1/50, v_0 = 3/100, k = 1$).

---

> [!question] Exemple 4.13 — Option Binaire dans le Modèle de Heston (Slides 144-145)
> - **Pay-off :** Option binaire européenne $X = H(S^1_T - K) = \mathbb{1}_{\{S^1_T \ge K\}}$.
> - **Objectif :** Évaluer le prix $p(T, K)$ et donner son approximation de Taylor au second ordre.

> [!success] Correction détaillée : Exemple 4.13
> 
> Par conditionnement sur la variance intégrée $\Upsilon_T$ (Eq. 141) :
> $$p(T, K) = \mathbb{E}_Q[p_{BS}(T, K, \Upsilon_T)] \quad \text{avec} \quad p_{BS}(T, K, \Upsilon) = e^{-rT} N(d_-)$$
> En effectuant un développement de Taylor au second ordre en puissances de $\Upsilon_T - \mathbb{E}_Q[\Upsilon_T]$ (Eq. 142-143) :
> $$p(T, K) = p_{BS}(T, K, \mathbb{E}_Q[\Upsilon_T]) + \frac{1}{2} \frac{\partial^2 p_{BS}}{\partial \Upsilon_T^2}(T, K, \mathbb{E}_Q[\Upsilon_T]) \operatorname{var}_Q[\Upsilon_T] + \dots$$
> où le terme de dérivée seconde s'exprime par :
> $$\frac{\partial^2}{\partial \Upsilon^2} N(d_-) = N'(d_-) \left( d''_2 - d_-(d'_-)^2 \right)$$
> La correction apportée à Black-Scholes est directement proportionnelle à la variance de la variance intégrée $\operatorname{var}_Q[\Upsilon_T]$ donnée par la formule (135).

---

> [!question] Exemple 4.16 — Non-existence d'E.M.M. (Densité $\xi$ surmartingale stricte) (Slides 150-154)
> - **Cadre :** $N = 3, W$ brownien 3-dim, $B_t = W_t + a$ avec $0 \ne a \in \mathbb{R}^3$.
>   $$d\tilde{S}_t = D(\tilde{S}_t)\left( \frac{1}{|B_t|} B_t dt + |B_t| dB_t \right), \quad \gamma_t = \frac{B_t}{|B_t|^2}$$
> - **Objectif :** Démontrer que $\xi_t = \frac{|a|}{|B_t|}$ et que $\mathbb{E}[\xi_T] < 1 = \xi_0$, prouvant que $\xi$ est une surmartingale stricte et qu'il n'existe aucune E.M.M.

> [!success] Correction détaillée : Exemple 4.16
> 
> **1. Forme explicite de $\xi_t$ par la formule d'Itô (Slide 152) :**
> Posons $f(x) = |x|^{-1}$ sur $\mathbb{R}^3 \setminus \{0\}$.
> Ses dérivées partielles sont $\partial_i f(x) = -x_i |x|^{-3}$ et $\partial_i \partial_j f(x) = (3x_i x_j |x|^{-2} - \delta_{ij})|x|^{-3}$.
> Le laplacien s'annule identiquement : $\Delta f(x) = \sum_i (3x_i^2 |x|^{-5} - |x|^{-3}) = 3|x|^{-3} - 3|x|^{-3} = 0$.
> Par la formule d'Itô :
> $$df(B_t) = \nabla f(B_t) \cdot dB_t = -|B_t|^{-3} B_t \cdot dB_t = |B_t|^{-1} dM_t$$
> ce qui donne par intégration :
> $$\xi_t = \exp\left(M_t - \frac{1}{2}\langle M, M \rangle_t\right) = \frac{|a|}{|B_t|} \quad (\text{Eq. 153})$$
> 
> ---
> 
> **2. Calcul explicite de l'espérance en coordonnées sphériques (Slides 153-154) :**
> Comme $B_t \sim \mathcal{N}(a, t I_3)$ :
> $$C(t) = \mathbb{E}\left[ \frac{|a|}{|B_t|} \right] = \int_{\mathbb{R}^3} \frac{|a|}{|x|} \frac{e^{-\frac{1}{2t}|x-a|^2}}{(2\pi t)^{3/2}} dx$$
> En passant en coordonnées sphériques d'axe $a$, on intègre par rapport aux angles $\theta, \phi$, puis on effectue le changement de variable radial :
> $$C(t) = \int_0^\infty \left[ \exp\left(-\frac{1}{2}\left(s - \frac{|a|}{\sqrt{t}}\right)^2\right) - \exp\left(-\frac{1}{2}\left(s + \frac{|a|}{\sqrt{t}}\right)^2\right) \right] \frac{ds}{\sqrt{2\pi}}$$
> Ce qui se simplifie exactement en (Slide 154, Eq. 156) :
> $$\mathbb{E}[\xi_t] = N\left(\frac{|a|}{\sqrt{t}}\right) - N\left(-\frac{|a|}{\sqrt{t}}\right) = 2 \int_0^{\frac{|a|}{\sqrt{t}}} \frac{e^{-y^2/2}}{\sqrt{2\pi}} dy$$
> Pour tout $t > 0$, comme $\frac{|a|}{\sqrt{t}} < +\infty$, cette intégrale est **strictement inférieure à 1** :
> $$\mathbb{E}[\xi_t] < 1 = \xi_0, \quad \forall t > 0$$
> $\xi$ est une **surmartingale stricte** : il y a fuite de masse de probabilité à l'infini. Il n'existe donc **aucune mesure martingale équivalente (E.M.M.)**, et le marché admet un FLVR.

---

> [!question] Exemple 4.17 — Construction d'un FLVR (Slides 155-157)
> - **Énoncé :** Construire explicitement une opportunité de *Free Lunch with Vanishing Risk* dans le cadre de l'Exemple 4.16.

> [!success] Correction détaillée : Exemple 4.17
> 
> **1. Stratégie de portefeuille fractionnaire (Slide 156) :**
> Avec la fraction d'investissement $\hat{\Pi}_t = B_t / |B_t|^3$, on a :
> $$\hat{\Pi}_t \cdot dN_t = -dM_t, \quad \hat{\Pi}_t \cdot dA_t = \frac{1}{|B_t|^2} dt$$
> Par la formule d'Itô (Slide 157, Eq. 161) :
> $$V_t(1, \hat{\Pi}) = \exp\left( -M_t + \frac{1}{2}\langle M, M \rangle_t \right) = \frac{1}{\xi_t} = \frac{|B_t|}{|a|}$$
> Pour une dotation initiale nulle ($x = 0$) :
> $$V_t(0, \hat{\Pi}) = V_t(1, \hat{\Pi}) - 1 = \frac{|B_t|}{|a|} - 1, \quad \text{avec } V_0(0, \hat{\Pi}) = 0$$
> 
> ---
> 
> **2. Stratégie arrêtée et conclusion du Free Lunch :**
> On pose $\tau = \inf\{t \ge 0 : V_t(0, \hat{\Pi}) < 0\}$ et on considère le processus arrêté $\hat{\Pi}^\tau$.
> Alors $V_T(0, \hat{\Pi}^\tau) \ge 0$ presque sûrement et $\mathbb{P}(V_T(0, \hat{\Pi}^\tau) > 0) > 0$.
> La variable bornée $X = V_T(0, \hat{\Pi}^\tau) \wedge 1$ vérifie :
> $$0 \ne X \in \bar{\mathcal{K}} \cap L^\infty_+$$
> ce qui démontre rigoureusement l'existence d'un **Free Lunch with Vanishing Risk (FLVR)**.

---

> [!question] Exercice 4.18 — Dérive dépendant d'un temps d'arrêt (Slide 158)
> - **Dynamique :** $W$ brownien standard, $\mathcal{T} = \inf\{t : W_t^2 = 1-t\}$, marché $t \in [0, 1]$, $r = 0$, et :
>   $$dS_t = S_t \left( 2 W_t \mathbb{1}_{[0, \mathcal{T}]} dt + (1-t)^2 dW_t \right), \quad S_0 = 1$$
> - **Questions :**
>   1. Trouver l'ensemble $\mathcal{M}_e$ des mesures martingales équivalentes dans le marché $\mathcal{M}$.
>   2. Prouver qu'il existe un FLVR et le construire.

> [!success] Correction détaillée : Exercice 4.18
> 
> **1. Ensemble $\mathcal{M}_e$ des E.M.M. :**
> Le taux de prime de risque instantané est :
> $$\gamma_t = \frac{\mu_t - r}{\sigma_t} = \frac{2 W_t \mathbb{1}_{[0, \mathcal{T}]}}{(1-t)^2}$$
> Par le théorème de Girsanov, le candidat densité de martingale s'écrit :
> $$\xi_t = \exp\left( -\int_0^{t \wedge \mathcal{T}} \frac{2W_s}{(1-s)^2} dW_s - \frac{1}{2} \int_0^{t \wedge \mathcal{T}} \frac{4W_s^2}{(1-s)^4} ds \right)$$
> Or, au voisinage de $t = 1$, sur la frontière $\mathcal{T}$, $W_s^2 \approx 1-s$, de sorte que l'intégrale déterministe diverge :
> $$\int_0^1 \frac{W_s^2}{(1-s)^4} ds \sim \int_0^1 \frac{1-s}{(1-s)^4} ds = \int_0^1 \frac{1}{(1-s)^3} ds = +\infty$$
> La densité $\xi_t$ s'annule p.s. en $t = 1$ ($\mathbb{E}[\xi_1] = 0 < 1$).
> Il en résulte que **l'ensemble des E.M.M. est vide** :
> $$\mathcal{M}_e = \emptyset$$
> 
> ---
> 
> **2. Preuve et construction du FLVR :**
> Comme $\mathcal{M}_e = \emptyset$, le théorème fondamental de Delbaen-Schachermayer (FTAP) garantit l'existence d'un FLVR.
> On le construit en considérant la suite de stratégies arrêtées $\tau_n = \mathcal{T} \wedge (1 - 1/n)$ qui capturent la dérive positive $2W_t > 0$ avant la singularité terminale : la perte maximale tend uniformément vers 0 tandis que le gain terminal reste strictement positif avec probabilité non nulle, formant un **Free Lunch with Vanishing Risk**.
