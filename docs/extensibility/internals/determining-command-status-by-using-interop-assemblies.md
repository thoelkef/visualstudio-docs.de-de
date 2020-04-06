---
title: Bestimmen des Befehlsstatus mithilfe von Interop-Assemblys | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52bea32997b083cd13349a37201411e357f94a90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708714"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Bestimmen des Befehlsstatus mithilfe von Interopassemblys
Ein VSPackage muss den Status der Befehle nachverfolgen, die es verarbeiten kann. Die Umgebung kann nicht bestimmen, wann ein in Ihrem VSPackage behandelter Befehl aktiviert oder deaktiviert wird. Es liegt in der Verantwortung Ihres VSPackage, die Umgebung über Befehlszustände zu informieren, z. B. über den Status allgemeiner Befehle wie **Ausschneiden**, **Kopieren**und **Einfügen**.

## <a name="status-notification-sources"></a>Statusbenachrichtigungsquellen
 Die Umgebung empfängt Informationen über Befehle <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> über die VSPackages-Methode, die Teil <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> der VSPackage-Implementierung der Schnittstelle ist. Die Umgebung <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ruft die Methode des VSPackage unter zwei Bedingungen auf:

- Wenn ein Benutzer ein Hauptmenü oder ein Kontextmenü öffnet (durch <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Rechtsklick), führt die Umgebung die Methode für alle Befehle in diesem Menü aus, um ihren Status zu bestimmen.

- Wenn das VSPackage anfordert, dass die Umgebung die aktuelle Benutzeroberfläche (UI) aktualisiert. Diese Aktualisierung tritt als Befehle auf, die derzeit für den Benutzer sichtbar sind, z. B. die Gruppierung **Ausschneiden**, **Kopieren**und **Einfügen** auf der Standardsymbolleiste, aktiviert und deaktiviert werden als Reaktion auf Kontext- und Benutzeraktionen.

  Da die Shell mehrere VSPackages hostet, würde die Leistung der Shell unannehmbar beeinträchtigt, wenn jedes VSPackage abgefragt werden müsste, um den Befehlsstatus zu bestimmen. Stattdessen sollte Ihr VSPackage die Umgebung aktiv benachrichtigen, wenn sich die Benutzeroberfläche zum Zeitpunkt der Änderung ändert. Weitere Informationen zur Aktualisierungsbenachrichtigung finden Sie unter [Aktualisieren der Benutzeroberfläche](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Statusbenachrichtigungsfehler
 Wenn Ihr VSPackage die Umgebung nicht über eine Befehlsstatusänderung benachrichtigt, kann die Benutzeroberfläche in einen inkonsistenten Zustand gebracht werden. Denken Sie daran, dass alle Menü- oder Kontextmenübefehle vom Benutzer auf einer Symbolleiste platziert werden können. Daher reicht es nicht aus, die Benutzeroberfläche nur zu aktualisieren, wenn ein Menü oder Kontextmenü geöffnet wird.

## <a name="see-also"></a>Weitere Informationen
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementierung](../../extensibility/internals/command-implementation.md)
