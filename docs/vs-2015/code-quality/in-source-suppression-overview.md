---
title: Übersicht über die Quellen Unterdrückung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 63d405b0e62735c0c1e3d7bb716ea2db29bc19fe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651572"
---
# <a name="in-source-suppression-overview"></a>Übersicht über die Unterdrückung im Quellcode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die in-Source-Unterdrückung ist die Fähigkeit, Code Analyse Verletzungen in verwaltetem Code zu unterdrücken oder zu ignorieren, indem das **SuppressMessage** -Attribut zu den Code Segmenten hinzugefügt wird, die die Verstöße verursachen. Das **SuppressMessage** -Attribut ist ein bedingtes Attribut, das in den IL-Metadaten der verwalteten Codeassembly nur enthalten ist, wenn das CODE_ANALYSIS-Kompilierungs Symbol zur Kompilierzeit definiert ist.

 Verwenden C++Sie in/CLI die Makros CA_SUPPRESS_MESSAGE oder CA_GLOBAL_SUPPRESS_MESSAGE in der Header Datei, um das-Attribut hinzuzufügen.

 Sie sollten keine in-Source-Unterdrückungen für Releasebuilds verwenden, um zu verhindern, dass die in-Source-Unterdrückungs Metadaten versehentlich versendet werden. Aufgrund der Verarbeitungskosten der in-Source-Unterdrückung kann die Leistung der Anwendung auch durch Einbeziehen der in-Source-Unterdrückungs Metadaten beeinträchtigt werden.

> [!NOTE]
> Sie müssen diese Attribute nicht selbst manuell codieren. Weitere Informationen finden Sie unter Gewusst [wie: Unterdrücken von Warnungen mithilfe des Menü Elements](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). Das Menü Element ist für C++ Code nicht verfügbar.

## <a name="suppressmessage-attribute"></a>SuppressMessage-Attribut
 Wenn Sie im **Fehlerliste** mit der rechten Maustaste auf eine Code Analyse Warnung klicken und dann auf **Nachricht unterdrücken**klicken, wird entweder im Code oder in der globalen Unterdrückungsdatei des Projekts ein **SuppressMessage** -Attribut hinzugefügt.

 Das **SuppressMessage** -Attribut weist das folgende Format auf:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]

```

 [C++]

```
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")

```

 Ort:

- **Regel Kategorie** : die Kategorie, in der die Regel definiert ist. Weitere Informationen zu Code Analyse-Regel Kategorien finden Sie unter [Code Analyse für Warnungen für verwalteten Code](../code-quality/code-analysis-for-managed-code-warnings.md).

- **Regel-ID** : der Bezeichner der Regel. Die Unterstützung umfasst sowohl einen kurzen als auch einen langen Namen für den Regel Bezeichner. Der Kurzname ist "CAXXXX;". der lange Name ist "CAXXXX: friendlytykiame".

- **Begründung** : der Text, der verwendet wird, um den Grund für das Unterdrücken der Nachricht zu dokumentieren.

- Nach **richten-ID** : eindeutiger Bezeichner eines Problems für jede Nachricht.

- **Bereich** : das Ziel, für das die Warnung unterdrückt wird. Wenn das Ziel nicht angegeben ist, wird es auf das Ziel des Attributs festgelegt. Folgende Bereiche werden unterstützt:

  - Modul

  - Namespace

  - Ressource

  - Geben Sie Folgendes ein:

  - Member

- **Target** : ein Bezeichner, der verwendet wird, um das Ziel anzugeben, auf dem die Warnung unterdrückt wird. Er muss einen voll qualifizierten Elementnamen enthalten.

## <a name="suppressmessage-usage"></a>SuppressMessage-Verwendung
 Code Analyse Warnungen werden auf der Ebene unterdrückt, auf die eine Instanz des **SuppressMessage** -Attributs angewendet wird. Dies dient dazu, die Unterdrückungs Informationen eng mit dem Code zu verknüpfen, in dem die Verletzung auftritt.

 Die allgemeine Form der Unterdrückung schließt die Regel Kategorie und einen Regel Bezeichner ein, der eine optionale, lesbare Darstellung des Regel namens enthält. Ein auf ein Objekt angewendeter

 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

 Wenn es strenge Leistungs Gründe für das Minimieren von in-Source-Unterdrückungs Metadaten gibt, kann der Regelname selbst ausgelassen werden. Die Regel Kategorie und Ihre Regel-ID bilden zusammen einen ausreichend eindeutigen Regel Bezeichner. Ein auf ein Objekt angewendeter

 `[SuppressMessage("Microsoft.Design", "CA1039")]`

 Dieses Format wird aufgrund von wart barkeits Problemen nicht empfohlen.

## <a name="suppressing-multiple-violations-within-a-method-body"></a>Unterdrücken von mehreren Verstößen innerhalb eines Methoden Texts
 Attribute können nur auf eine Methode angewendet werden und können nicht in den Methoden Text eingebettet werden. Allerdings können Sie den Bezeichner als Nachrichten-ID angeben, um mehrere Vorkommen eines Verstoßes innerhalb einer Methode zu unterscheiden.

 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]

## <a name="generated-code"></a>Generierter Code
 Compiler verwalteter Code und einige Tools von Drittanbietern generieren Code, um eine schnelle Code Entwicklung zu ermöglichen. Vom Compiler generierter Code, der in Quelldateien angezeigt wird, wird normalerweise mit dem **GeneratedCodeAttribute** -Attribut markiert.

 Sie können auswählen, ob Warnungen und Fehler bei der Code Analyse für generierten Code unterdrückt werden sollen. Informationen dazu, wie Sie Warnungen und Fehler unterdrücken, finden Sie unter Gewusst [wie: Unterdrücken von Warnungen für generierten Code](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

 Beachten Sie, dass die Code Analyse **GeneratedCodeAttribute** ignoriert, wenn es auf eine gesamte Assembly oder einen einzelnen Parameter angewendet wird. Diese Situationen treten selten auf.

## <a name="global-level-suppressions"></a>Unterdrückungen auf globaler Ebene
 Das Tool für die Analyse von verwaltetem Code untersucht **SuppressMessage** -Attribute, die auf Assembly-, Modul-, Typ-, Element-oder Parameter Ebene angewendet werden. Außerdem werden Verstöße gegen Ressourcen und Namespaces ausgelöst. Diese Verstöße müssen auf globaler Ebene angewendet werden und sind auf einen Bereich beschränkt. Beispielsweise wird durch die folgende Meldung eine Namespace Verletzung unterdrückt:

 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Wenn Sie eine Warnung mit dem Namespace Bereich unterdrücken, wird die Warnung gegen den Namespace selbst unterdrückt. Die Warnung wird nicht für Typen im-Namespace unterdrückt.

 Alle Unterdrückungen können durch Angabe eines expliziten Bereichs ausgedrückt werden. Diese Unterdrückungen müssen auf globaler Ebene aktiv sein. Sie können die Unterdrückung auf Element Ebene nicht angeben, indem Sie einen Typ ergänzen.

 Unterdrückungen auf globaler Ebene sind die einzige Möglichkeit, Nachrichten zu unterdrücken, die auf vom Compiler generierten Code verweisen, der der explizit bereitgestellten Benutzer Quelle nicht zugeordnet ist. Der folgende Code unterdrückt z. b. einen Verstoß gegen einen vom Compiler ausgegebenen Konstruktor:

 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> Das Ziel enthält immer den voll qualifizierten Elementnamen.

## <a name="global-suppression-file"></a>Globale Unterdrückungs Datei
 Die globale Unterdrückungs Datei verwaltet Unterdrückungen, bei denen es sich entweder um Unterdrückungen auf globaler Ebene oder um Unterdrückungen handelt, die kein Ziel angeben. Beispielsweise werden Unterdrückungen für Verstöße auf Assemblyebene in dieser Datei gespeichert. Außerdem werden einige ASP.net Unterdrückungen in dieser Datei gespeichert, da Einstellungen auf Projektebene für Code hinter einem Formular nicht verfügbar sind. Eine globale Unterdrückung wird erstellt und dem Projekt hinzugefügt, wenn Sie zum ersten Mal die Option **in der Projekt Unterdrückungs Datei** des Befehls unter **drücken der Nachricht (en)** im Fehlerliste Fenster auswählen. Weitere Informationen finden Sie unter Gewusst [wie: Unterdrücken von Warnungen mithilfe des Menü Elements](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).

## <a name="see-also"></a>Siehe auch
 <xref:System.Diagnostics.CodeAnalysis>
