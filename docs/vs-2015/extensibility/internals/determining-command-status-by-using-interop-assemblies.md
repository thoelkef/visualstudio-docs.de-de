---
title: Bestimmen des Befehls Status mithilfe von Interop-Assemblys | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc67123e082258932ab5df6613941f869d6049a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196790"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Bestimmen des Befehlsstatus mithilfe von Interop-Assemblys
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein VSPackage muss den Status der Befehle nachverfolgen, die er verarbeiten kann. Die Umgebung kann nicht bestimmen, wann ein Befehl, der in Ihrem VSPackage behandelt wird, aktiviert oder deaktiviert wird. Es liegt in der Verantwortung des VSPackages, die Umgebung über Befehls Zustände zu informieren, z. b. den Status allgemeiner Befehle wie **Ausschneiden**, **Kopieren**und **Einfügen**.  
  
## <a name="status-notification-sources"></a>Status Benachrichtigungs Quellen  
 Die Umgebung empfängt Informationen über Befehle über die VSPackages <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> -Methode, die Teil der VSPackage-Implementierung der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle ist. Die Umgebung Ruft die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode des VSPackage unter zwei Bedingungen auf:  
  
- Wenn ein Benutzer ein Hauptmenü oder ein Kontextmenü öffnet (indem Sie mit der rechten Maustaste klicken), führt die Umgebung die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode für alle Befehle in diesem Menü aus, um deren Status zu ermitteln.  
  
- Wenn das VSPackage anfordert, dass die Umgebung die aktuelle Benutzeroberfläche aktualisiert (UI). Dies geschieht als Befehle, die für den Benutzer derzeit sichtbar sind, wie z. b. die Gruppierung zum **Ausschneiden**, **Kopieren**und **Einfügen** auf der Standard Symbolleiste, als Reaktion auf Kontext-und Benutzeraktionen aktiviert und deaktiviert werden.  
  
  Da die Shell mehrere VSPackages hostet, kann die Leistung der Shell nicht beeinträchtigt werden, wenn jedes VSPackage abgerufen werden musste, um den Befehlsstatus zu ermitteln. Stattdessen sollte das VSPackage die Umgebung aktiv Benachrichtigen, wenn die Benutzeroberfläche zum Zeitpunkt der Änderung geändert wird. Weitere Informationen zur Aktualisierungs Benachrichtigung finden Sie unter [Aktualisieren der Benutzeroberfläche](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Status Benachrichtigungs Fehler  
 Wenn das VSPackage fehlschlägt, um die Umgebung über eine Änderung des Befehls Zustands zu benachrichtigen, kann die Benutzeroberfläche in einen inkonsistenten Zustand versetzt werden. Denken Sie daran, dass die Befehle des Menüs oder des Kontextmenüs vom Benutzer auf einer Symbolleiste abgelegt werden können. Daher reicht es nicht aus, die Benutzeroberfläche zu aktualisieren, wenn ein Menü oder ein Kontextmenü geöffnet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementierung](../../extensibility/internals/command-implementation.md)
