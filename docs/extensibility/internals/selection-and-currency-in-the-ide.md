---
title: Auswahl und Währung in der IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f580b7c8e1651dcbcd053476ae756399a0ac3482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705572"
---
# <a name="selection-and-currency-in-the-ide"></a>Auswahl und Aktualität in der IDE
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) verwaltet Informationen über die aktuell ausgewählten Objekte der Benutzer mithilfe des *Auswahlkontexts*. Mit dem Auswahlkontext kann VSPackages auf zwei Arten am Währungstracking teilnehmen:

- Durch Weitergeben von Währungsinformationen über die VSPackages an die IDE.

- Durch Überwachen der aktuell aktiven Auswahl der Benutzer innerhalb der IDE.

## <a name="selection-context"></a>Auswahlkontext
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE verfolgt die IDE-Währung global in ihrem eigenen globalen Auswahlkontextobjekt. Die folgende Tabelle zeigt die Elemente, aus denen sich der Auswahlkontext ergibt.

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Aktuelle Hierarchie|In der Regel das aktuelle Projekt; Eine aktuelle NULL-Hierarchie gibt an, dass die Lösung als Ganzes aktuell ist.|
|Aktuelle ItemID|Das ausgewählte Element innerhalb der aktuellen Hierarchie; Wenn mehrere Auswahlen in einem Projektfenster vorhanden sind, können mehrere aktuelle Elemente vorhanden sein.|
|Aktuellen`SelectionContainer`|Enthält die einen oder mehrere Objekte, für die das Eigenschaftenfenster Eigenschaften anzeigen soll.|

 Darüber hinaus verwaltet die Umgebung zwei globale Listen:

- Eine Liste der aktiven UI-Befehlsbezeichner

- Eine Liste der aktuell aktiven Elementtypen.

### <a name="window-types-and-selection"></a>Fenstertypen und Auswahl
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organisiert Fenster in zwei allgemeine Typen:

- Fenster vom Typ Hierarchie

- Rahmenfenster, z. B. Werkzeug- und Dokumentfenster

  Die IDE verfolgt die Währung für jeden dieser Fenstertypen unterschiedlich.

  Das häufigste Projekttypfenster ist der Projektmappen-Explorer, den die IDE steuert. Ein Projektfenster verfolgt die globale Hierarchie und die ItemID des globalen Auswahlkontexts, und das Fenster basiert auf der Auswahl des Benutzers, um die aktuelle Hierarchie zu bestimmen. Für Projektfenster stellt die Umgebung den <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>globalen Dienst bereit, über den VSPackages die aktuellen Werte für geöffnete Elemente überwachen kann. Das Durchsuchen von Eigenschaften in der Umgebung wird von diesem globalen Dienst gesteuert.

  Framefenster hingegen verwenden das DocObject innerhalb des Rahmenfensters, um den SelectionContext-Wert (das Trio hierarchie/ItemID/SelectionContainer) zu drücken. . Rahmenfenster verwenden <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> den Dienst zu diesem Zweck. Das DocObject kann nur Werte für den Auswahlcontainer verschieben, wobei die lokalen Werte für Hierarchie und ItemID unverändert bleiben, wie dies für untergeordnete MDI-Dokumente typisch ist.

### <a name="events-and-currency"></a>Veranstaltungen und Währung
 Es können zwei Arten von Ereignissen auftreten, die sich auf den Währungsbegriff der Umgebung auswirken:

- Ereignisse, die auf die globale Ebene weitergegeben werden und den Fensterrahmenauswahlkontext ändern. Beispiele für diese Art von Ereignis sind das Öffnen eines MDI-Untergeordneten Fensters, das Öffnen eines globalen Werkzeugfensters oder das Öffnen eines Projekt-Werkzeugfensters.

- Ereignisse, die die Elemente ändern, die im Fensterrahmenauswahlkontext nachverfolgt werden. Beispiele hierfür sind das Ändern der Auswahl innerhalb eines DocObject oder das Ändern der Auswahl in einem Projekttypfenster.

## <a name="see-also"></a>Weitere Informationen
- [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md)
- [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md)
