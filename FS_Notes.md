## <center> Rechnerregeln

- L1/L2 = L1 intersect !L2
  
![Rules](1.png)
![Rules2](2.png)

----
## <center> Grammatiken

- **Satz**: Es gibt *abzählbar* viele Wörter über jedem Alphabet Σ. Jede Sprache ist also entweder endlich oder abzählbar unendlich.
- Eine Menge M ist abzählbar gdw. es eine injektive Funktion f : M → N gibt
- **Satz**: Es gibt *überabzählbar*  viele Sprachen über jedem beliebigen Alphabet Σ
- Die Menge der DFAs ist abzahlbar
-  Die Kardinalität der Potenzmenge ist immer größer als die der Menge selbst
  
- Eine Grammatik G ist ein 4-Tupel G = hV, Σ, P, Si bestehend aus:
  - V eine Menge von Variablennamen,
  - Σ ein Alphabet, disjunkt zu V (d.h., Σ ∩ V = ∅),
  - P eine Menge von Produktionsregeln der Form w → v für beliebige Wörter w und
v über Σ ∪ V, wobei w mindestens eine Variable enthält (d.h. w, v ∈ (Σ ∪ V)∗ und w !∈ Σ∗),
  - S eine Startvariable aus V (d.h. S ∈ V).
Die Elemente von Σ nennt man auch Terminalsymbole, die Elemente von V analog
Nichtterminalsymbole.
---
- Eine Grammatik G = hV, Σ, P, Si ist genau dann von Typ 1 (kontextsensitiv), wenn eine
der folgenden Bedingungen gilt:
 - 1) Alle Regeln w → v erfüllen die Bedingung |w| ≤ |v| (ursprüngliche Definition).
 - 2) Es gibt eine Regel S → e und alle anderen Regeln w → v erfüllen zwei
Bedingungen:
    - a) |w| ≤ |v| (insbesondere ist also v , e);
    - b) S kommt nicht in v vor.
(Sonderfall mit einer einzelnen e-Regel.)
<br></br>
- Eine kontextfreie Grammatik G = hV, Σ, P, Si ist e-frei, wenn eine der folgenden Bedingungen gilt:
    - 1) Es gibt keine Regel der Form A → e
    - 2) Es gibt eine Regel S →e und bei allen anderen Regeln A → v ist v , e und S
kommt nicht in v vor.


e-freie kontextfreie Grammatiken erzeugen die gleichen
Sprachen wie kontextfreie Grammatiken allgemein

---

## <center> DFA, NFA

Ein deterministischer endlicher Automat (international: „DFA“, deterministic finite automaton) M ist ein Tupel M = hQ, Σ, δ, q0, Fi mit den folgenden Bestandteilen:
- Q: endliche Menge von Zuständen
- Σ: Alphabet
- δ: Übergangsfunktion, eine partielle∗ Funktion Q × Σ → Q
- q0: Startzustand q0 ∈ Q
- F: Menge von Endzuständen F ⊆ Q

**Satz**: Mtotal = (Q`, Σ, δ`, q0, F) hat eine totale Übergangsfunktion und akzeptiert die selbe Sprache wie M, d.h. L(Mtotal) = L(M).

**Satz**: Die Klasse der Sprachen, die durch einen DFA erkannt werden können, ist genau die Klasse der regulären Sprachen.

Ein **nichtdeterministischer** endlicher Automat (international: „NFA“) M ist ein Tupel
M = hQ, Σ, δ, Q0, Fi mit folgenden Bestandteilen:
- Q: endliche Menge von Zuständen,
- Σ: Alphabet,
- δ: Übergangsfunktion, eine totale Funktion Q × Σ → 2^Q, wobei 2^Q die
Potenzmenge von Q ist;
- Q0: Menge möglicher Startzustände Q0 ⊆ Q,
- F: Menge von Endzuständen F ⊆ Q
---
- Ein DFA hat genau einen Lauf für jedes Wort.
Er akzeptiert, wenn dieser Lauf akzeptierend ist.
- Ein NFA kann für ein Wort mehrere Läufe haben.
Er akzeptiert, wenn einer dieser Läufe akzeptierend ist.
- Die Sprache eines NFA M = hQ, Σ, δ, Q0, Fi ist die Menge aller Wörter w ∈Σ∗, für die M einen akzeptierenden Lauf hat.
- Die Sprache eines NFA M = hQ, Σ, δ, Q0, Fi ist L(M) = {w ∈ Σ∗
| δ(Q0, w) ∩ F != ∅}
- Ein endlicher Automat M ist genau dann äquivalent zu einem endlichen Automaten M0, wenn L(M) = L(M0) gilt
- Jeder DFA kann als NFA aufgefasst werden. Daher wird jede von einem DFA
akzeptierbare Sprache auch von einen NFA akzeptiert.
- **Satz**: Jede von einem NFA akzeptierbare Sprache wird auch von einen DFA akzeptiert
- **Satz**: Die Klasse der Sprachen, die durch DFAs oder NFAs erkannt werden können,ist genau die Klasse der regulären Sprachen
- NFA mit Wortübergangen: Die Sprache solcher Automaten wird wie bei NFAs definiert, nur dass in einem Schritt
beliebige Wörter gelesen werden können.
- **Satz**: Jede von einem NFA mit Wortübergängen akzeptierte Sprache wird auch von einem „normalen“ NFA akzeptiert.

### E-NFA Variationen
- Die Konstruktion im Beweis „verlängert“ normale Übergänge „nach rechts“ durch Anhängen von e-Transitionen.
- Verlängerung nach links“:e-Transitionen vor normalen Übergängen;
Anfangszustände werden beibehalten; dafür werden Endzustände mit
e-Transitionen erweitert.
----
### Abschluss eigenschaften
- Schnitt: Akzeptiere genau dann, wenn beide Automaten akzeptieren (Produktautomat, alle mögliche Paare Q1 × Q2, Σ, δ, Q0,1 × Q0,2, F1 × F2)
  - Satz: L(M1 ⊗ M2) = L(M1) ∩ L(M2).
- Vereinigung: akzeptiere wenn einer der Automaten akzeptiert
  - Satz: L(M1 ⊕ M2) = L(M1) ∪ L(M2).
- Komplement
  - **Satz**: Für jeden DFA M mit **totaler Übergangsfunktion** gilt L(!M) = !L(M).
  - Auch NFAs dürfen nicht direkt komplementiert werden:
- Konkatenation
  - Wir können Automaten „hintereinander hängen“, indem wir von Endzuständen des
ersten zu Startzuständen des zweiten wechseln.
  - Satz: Für alle NFA M1 und M2 gilt L(M1  M2) = L(M1) ◦ L(M2).
- Kleene-Stern
  - Der Kleene-Stern ist eine verallgemeinerte Konkatenation, bei der ein Automat
rekursiv hinter sich selbst „gehängt“ wird.
  - Satz: L(M∗) = L(M)∗
  
Der Vereinigungsautomat ist immer ein NFA

----

## <center> Reguläre Ausdrücke

**Satz**: Jede endliche Sprache ist regulär

**Satz**: Alle regulären Sprachen können durch Anwendung von ∪, ◦ und ∗ aus endlichen Sprachen konstruiert werden

Zwei reguläre Ausdrücke α und β sind genau dann äquivalent, in Symbolen α ≡ β, wenn L(α) = L(β).
  - ∅∗ ≡ e
  - e* = e

Eine Sprache L ist genau dann regulär, wenn es einen regulären
Ausdruck α gibt, für den L(α) = L gilt.
  -  Für jeden regulären Ausdruck α gibt es einen NFA M, so dass L(α) = L(M)
  -  Für jeden NFA M gibt es einen regulären Ausdruck α, so dass L(α) = L(M)

Regel von Arden: Aus α ≡ βα | γ mit e not aus L(β) folgt α ≡ β∗γ.

## <center> Minimal Automaten

- Unterschiedliche Äquivalenzklassen sind disjunkt:
- Für einen DFA M = (Q, Σ, δ, q0, Fi) mit totaler Übergangsfunktion ist der
Quotientenautomat M/∼ gegeben durch M/∼ = (Q/∼, Σ, δ∼, [q0]∼M , F/∼), wobei gilt:
  - Q/∼ = {[q]∼ | q ∈ Q}
  - δ∼([q]∼, a) = [δ(q, a)]∼
  - F/∼ = {[q]∼ | q ∈ F}
- **Satz**: Für jeden totalen DFA M gilt L(M) = L(M/∼)
  - (1) Aus q1 ∼ q2 folgt stets: q1 ∈ F gdw. q2 ∈ F.
  - (2) Wenn q1 ∼ q2, dann auch δ(q1, a) ∼ δ(q2, a).
  - (1) Aus q1 ∈ F und q2 < F folgt immer q1 / q2.
  - (2) Wenn δ(q1, a) / δ(q2, a), dann q1 / q2.

Sei M ein DFA mit totaler Übergangsfunktion. Der reduzierte Automat Mr ergibt sich durch folgende Schritte (minimalen DFA):
- (1) Entferne alle unerreichbaren Zustände aus M.
- (2) Berechne den Quotientenautomaten.

**Satz**: Alle minimalen DFA mit totaler Übergangsfunktion, die L(M) erkennen, sind bis auf Umbenennung von Zuständen gleich (sie sind isomorph). Daher hängt Mr nur von L(M) ab, nicht von M.

Für eine Sprache L ⊆ Σ∗ ist die Nerode-Rechtskongruenz 'L wie folgt definiert:

    Für Wörter u, v ∈ Σ∗ sei u 'L v genau dann, wenn gilt:
    Für alle w ∈ Σ∗ gilt: uw ∈ L genau dann, wenn vw ∈ L

Definition (kurz): u ~ v gdw. für alle w ∈ Σ∗ gilt: uw ∈ L gdw. vw ∈ L.

**Satz (Myhill & Nerode)**: Eine Sprache L ist genau dann regulär, wenn 'L endlich viele Äquivalenzklassen hat.

**Satz**: M( Myhill-Nerode-Minimalautomat) hat unter allen totalen DFAs, die L erkennen, eine minimale Anzahl an Zuständen.

Ein Isomorphismus zwischen zwei DFAs M1 = (Q1, Σ, δ1, q1, F1) und
M2 = (Q2, Σ, δ2, q2, F2) ist eine bijektive Funktion f : Q1 → Q2, so dass gilt:
- f(q1) = q2
- f(δ1(q, a)) = δ2(f(q), a) für alle a ∈ Σ
- {f(q) | q ∈ F1} = F2
Zwei Automaten sind isomorph, wenn es einen Isomorphismus zwischen ihnen gibt.

**Satz**: Ist L eine reguläre Sprache, M ein DFA mit totaler Übergangsfunktion und L(M) = L, so sind der reduzierte Automat Mr und der Myhill-Nerode-Minimalautomat ML isomorph.
  - also ML ist isomorph zu jedem reduzierten Automaten für L.

### Testen ob 2 Automaten gleiche Sprache erzeugen
  - Transformiere M1 und M2 falls nötig in DFAs mit totaler Übergangsfunktion
  - Bestimme die reduzierten Automaten
  -  Teste, ob die reduzierten Automaten isomorph sind (z.B. naiv durch
systematisches Durchprobieren aller Bijektionen)









