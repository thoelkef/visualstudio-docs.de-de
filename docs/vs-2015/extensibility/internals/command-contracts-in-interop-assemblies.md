---
title: Befehls Verträge in Interop-Assemblys | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50d48d3a8ff55559cce1c3a40142e31b8eebd85f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195125"
---
# <a name="command-contracts-in-interop-assemblies"></a>Befehlsverträge in Interop-Assemblys
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der grundlegende Vertrag für die Handhabung von Befehlen über die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle besteht darin, dass die Umgebung die-Methode aufruft, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> um zu bestimmen, ob der Befehl unterstützt wird, und, falls unterstützt, seinen Zustand und Text zu bestimmen. Dann ruft die Umgebung die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode auf, um den Befehl auszuführen.  
  
 Die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode wird für alle Befehle identisch behandelt. Die weitere Kommunikation, falls erforderlich (z. b. mit Dropdown Listen), wird durch Aufrufen der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode mit den entsprechenden Parametern verwaltet. Die Interpretation dieser Parameter hängt von dem angegebenen Befehl ab.  
  
 Wenn das Befehls Ziel Werte im Output-Parameter zurückgibt, ist der Aufrufer immer dafür verantwortlich, alle zugeordneten Ressourcen freizugeben. Da dieser Parameter eine Variante ist, werden die Ressourcen durch das Löschen der Variante freigegeben.  
  
 In Fällen, in denen-Befehle innerhalb eines Hierarchie Fensters funktionieren müssen, muss die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle verwendet werden. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> -Schnittstelle verfügt über einen ähnlichen Vertrag mit ähnlichen Methoden: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehls Routing in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementierung](../../extensibility/internals/command-implementation.md)
