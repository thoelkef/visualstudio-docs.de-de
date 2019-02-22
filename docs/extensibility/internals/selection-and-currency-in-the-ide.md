---
title: Auswahl und Aktualität in der IDE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0db376b57c6f581137b2bf48fbc5d354651a8ef6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56653956"
---
# <a name="selection-and-currency-in-the-ide"></a>Auswahl und Aktualität in der IDE
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) verwaltet Informationen zu Benutzer ausgewählte Objekte derzeit mit der Auswahl *Kontext*. Mit Auswahlkontext können VSPackages Teil in der Währung, die nachverfolgung auf zwei Arten ausführen:

-   Verbreiten Sie Informationen zu Währungen finden Informationen zu den VSPackages in der IDE.

-   Durch die Überwachung von derzeit aktiven Auswahl von Benutzern in der IDE.

## <a name="selection-context"></a>Auswahlkontext
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Global verfolgt des IDE-Währung, in eine eigene globale Auswahl Context-Objekt. Die folgende Tabelle zeigt die Elemente, die den Auswahlkontext bilden.

|Element|Beschreibung|
|-------------|-----------------|
|Aktuellen Hierarchie|In der Regel das aktuelle Projekt; eine aktuelle Hierarchie von NULL gibt an, dass die Projektmappe als Ganzes aktuell ist.|
|Aktuelle Element-ID|Das ausgewählte Element in der aktuellen Hierarchie Wenn die Mehrfachauswahl in einem Projektfenster sind, können mehrere aktuelle Elemente vorhanden sein.|
|Aktuelle `SelectionContainer`|Enthält, die eine oder mehrere Objekte, die für die Eigenschaften im Eigenschaftenfenster angezeigt werden soll.|

 Darüber hinaus behält die Umgebung zwei globale Listen:

-   Eine Liste der aktiven UI-Befehls-IDs

-   Eine Liste der derzeit aktiven Elementtypen.

### <a name="window-types-and-selection"></a>Fenstertypen und Auswahl
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organisiert Windows in zwei allgemeine Typen:

- Hierarchy-Datentyp-windows

- Frame-Fenster, z. B. Tool-und Dokumentfenster

  Die IDE verfolgt Währung unterschiedlich für jedes dieser Fenster-Typen.

  Das am häufigsten verwendete Projekttyp-Fenster wird im Projektmappen-Explorer die steuert, die IDE. Ein Fenster Projekttyp verfolgt nach, die globalen Hierarchie und Element-ID des Kontexts globale Auswahl, und im Fenster auf die Auswahl des Benutzers bestimmen die aktuelle Hierarchie basiert. Projekttyp unter Windows enthält die Umgebung beim globalen Dienst <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, über welche VSPackages können die aktuellen Werte für geöffneten Elemente überwachen. Navigieren in der Umgebung Eigenschaft wird von diesem globalen Dienst gesteuert.

  Rahmenfenster, verwenden das Objekt auf der anderen Seite in das Rahmenfenster den SelectionContext-Wert (der Hierarchie/ItemID/SelectionContainer Trio) mithilfe von Push übertragen. . Frame-Fensters mithilfe des Diensts <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> für diesen Zweck. Das Objekt kann mithilfe von Push übertragen nur Werte für den Auswahlcontainer, verlassen die lokalen Werte für die Hierarchie und Element-ID unverändert, typischerweise für untergeordnete MDI-Dokumente.

### <a name="events-and-currency"></a>Ereignisse und Währung
 Zwei Arten von Ereignissen auftreten, die der Umgebung Konzept der Währung beeinflussen:

-   Ereignisse, die auf globaler Ebene weitergegeben werden, und ändern Sie den Auswahlkontext für Fenster-Frames. Beispiele für diese Art von Ereignissen sind ein untergeordnetes MDI-Fenster geöffnet wird, ein globaler Toolfenster geöffnet wird, oder ein Projekttyp-Toolfenster geöffnet wird.

-   Ereignisse, die die Elemente, die in den Auswahlkontext für Fenster-Frames wird nachverfolgt, zu ändern. Beispiele: Ändern der Auswahl im DocObject oder Ändern der Auswahl in einem Projekttyp-Fenster.

## <a name="see-also"></a>Siehe auch
- [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md)
- [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md)