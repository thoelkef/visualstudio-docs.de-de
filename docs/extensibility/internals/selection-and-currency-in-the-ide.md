---
title: Auswahl und Währung in der IDE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edff400420ca5f0c93e1df85fb9118eee6302d02
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723963"
---
# <a name="selection-and-currency-in-the-ide"></a>Auswahl und Aktualität in der IDE
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) verwaltet Informationen zu den derzeit ausgewählten Objekten der Benutzer mithilfe des Auswahl *Kontexts*. Mit dem Auswahl Kontext können VSPackages in zweierlei Hinsicht an der Währungs Nachverfolgung teilnehmen:

- Durch die Weitergabe von Währungsinformationen über die VSPackages an die IDE.

- Durch Überwachen der derzeit aktiven Auswahl von Benutzern in der IDE.

## <a name="selection-context"></a>Auswahl Kontext
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE verfolgt Global die IDE-Währung in einem eigenen globalen Auswahl Kontext Objekt. In der folgenden Tabelle werden die Elemente angezeigt, die den Auswahl Kontext bilden.

|Element|Beschreibung|
|-------------|-----------------|
|Aktuelle Hierarchie|In der Regel das aktuelle Projekt; eine aktuelle NULL-Hierarchie gibt an, dass die gesamte Projekt Mappe aktuell ist.|
|Aktuelle Itemid|Das ausgewählte Element innerhalb der aktuellen Hierarchie. Wenn in einem Projektfenster mehrere Auswahlmöglichkeiten vorhanden sind, können mehrere aktuelle Elemente vorhanden sein.|
|Aktuelle `SelectionContainer`|Enthält das mindestens ein-Objekt, für das die Eigenschaftenfenster Eigenschaften anzeigen soll.|

 Außerdem verwaltet die Umgebung zwei globale Listen:

- Eine Liste aktiver UI-Befehls Bezeichner

- Eine Liste der derzeit aktiven Elementtypen.

### <a name="window-types-and-selection"></a>Fenstertypen und-Auswahl
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organisiert Fenster in zwei allgemeinen Typen:

- Hier archietyp Fenster

- Rahmen Fenster, z. b. Tool-und Dokument Fenster

  Die IDE verfolgt die Währung für jeden dieser Fenstertypen anders.

  Das gängigste Projekttyp Fenster ist der Projektmappen-Explorer, der von der IDE gesteuert wird. Ein Projekttyp Fenster verfolgt die globale Hierarchie und die Itemid des globalen Auswahl Kontexts. das Fenster basiert auf der Auswahl des Benutzers, um die aktuelle Hierarchie zu bestimmen. Für Projekttyp Fenster stellt die Umgebung den globalen Dienst <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> bereit, über den VSPackages die aktuellen Werte für geöffnete Elemente überwachen können. Das Durchsuchen von Eigenschaften in der Umgebung wird durch diesen globalen Dienst gesteuert.

  Rahmen Fenster verwenden hingegen das DocObject-Objekt im Rahmen Fenster, um den selectioncontext-Wert (Hierarchie/Itemid/SelectionContainer-Trio) zu übersetzen. sein. Rahmen Fenster verwenden den Dienst <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> zu diesem Zweck. Das DocObject-Objekt kann nur Werte für den Auswahl Container per Push Übertragung, wobei die lokalen Werte für die Hierarchie und die Itemid unverändert bleiben, was für untergeordnete MDI-Dokumente typisch ist.

### <a name="events-and-currency"></a>Ereignisse und Währung
 Es können zwei Arten von Ereignissen auftreten, die sich auf das Konzept der Umgebung der Umgebung auswirken:

- Ereignisse, die an die globale Ebene weitergegeben werden und den Fensterrahmen-Auswahl Kontext ändern. Beispiele für diese Art von Ereignis sind das Öffnen eines untergeordneten MDI-Fensters, das Öffnen eines globalen Tool Fensters oder das Öffnen eines Projekttyp-Tool Fensters.

- Ereignisse, die die Elemente ändern, die innerhalb des Fensterrahmen-Auswahl Kontexts verfolgt werden. Beispiele hierfür sind das Ändern der Auswahl in einem DocObject oder das Ändern der Auswahl in einem Projekttyp Fenster.

## <a name="see-also"></a>Siehe auch
- [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md)
- [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md)