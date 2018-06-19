---
title: Bestimmen mithilfe von Interop-Assemblys Befehlsstatus | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4989910fdec968a4a05e2459e6625ee2c15fd9a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128168"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Bestimmen der Befehlsstatus mithilfe von Interop-Assemblys
Eine VSPackage muss den Status der Befehle von verfolgt, die sie behandeln kann. Die Umgebung kann nicht bestimmt werden, wenn ein Befehl innerhalb Ihres VSPackage behandelt aktiviert oder deaktiviert wird. Es handelt sich um die Zuständigkeit für das VSPackage, um die Umgebung zum Befehl Status zu informieren, z. B. der Status der allgemeine Befehle wie **Ausschneiden**, **Kopie**, und **einfügen**.  
  
## <a name="status-notification-sources"></a>Status-Benachrichtigung-Quellen  
 Die Umgebung empfängt Informationen zu Befehlen durch den VSPackages' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, die Teil der VSPackage Implementierung ist von der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode des VSPackage unter zwei Bedingungen:  
  
-   Wenn ein Benutzer eine Hauptmenü oder ein Kontextmenü (indem Sie mit der rechten Maustaste) geöffnet wird, führt die Umgebung die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode auf alle Befehle in diesem Menü, um ihren Status zu bestimmen.  
  
-   Wenn das VSPackage anfordert, dass die Umgebung die aktuelle Benutzeroberfläche (UI) aktualisieren. In diesem Fall als Befehle ein, die derzeit für den Benutzer sichtbar, z. B. sind die **Ausschneiden**, **Kopie**, und **einfügen** auf der Standardsymbolleiste gruppieren, werden aktiviert und deaktiviert Antwort auf die Aktionen "Kontext" und Benutzer.  
  
 Da die Shell mehrere VSPackages hostet, würde der Shell Leistung unannehmbar beeinträchtigt werden, sofern dies für jedes VSPackage erkundigen Befehlsstatus abrufen erforderlich waren. Stattdessen sollten das VSPackage aktiv Umgebung benachrichtigen, wenn zum Zeitpunkt der Änderung die Benutzeroberfläche ändert. Weitere Informationen zu updatebenachrichtigung, finden Sie unter [Aktualisieren der Benutzeroberfläche](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Fehler beim Status-Benachrichtigung  
 Fehler Ihres VSPackage die Umgebung eine statusänderung Befehl benachrichtigen kann die Benutzeroberfläche in einem inkonsistenten Zustand platzieren. Denken Sie daran, dass die Menübefehle Menü- oder Kontext auf einer Symbolleiste vom Benutzer platziert werden können. Deshalb reicht Aktualisierung der Benutzeroberfläche nur, wenn ein Menü oder im Kontextmenü öffnet nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Elemente der Benutzeroberfläche hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementation (Implementierung)](../../extensibility/internals/command-implementation.md)