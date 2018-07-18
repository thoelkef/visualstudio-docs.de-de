---
title: Befehl Verträge im Interop-Assemblys | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfb60bb4fdc0a633ecee92c47b8465f794416bec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127375"
---
# <a name="command-contracts-in-interop-assemblies"></a>Befehl Verträge im Interop-Assemblys
Die grundlegende Vertrag für die Behandlung von Befehlen über die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle ist, dass die Umgebung Ruft die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, um zu bestimmen, ob der Befehl unterstützt wird und, falls dies unterstützt wird, um dessen Status und den Text zu bestimmen. Anschließend ruft die Umgebung die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode zum Ausführen des Befehls.  
  
 Die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode ist für alle Befehle identisch behandelt. Weitere Kommunikation, bei Bedarf (z. B. mit Dropdown-Listen), erfolgt durch Aufrufen der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode mit dem entsprechenden Parameter. Die Interpretation dieser Parameter hängt von den angegebenen Befehl ab.  
  
 Wenn das Befehlsziel Werte in der Output-Parameter zurückgibt, ist der Aufrufer immer verantwortlich für die Freigabe von Ressourcen, die zugeordnet wurde. Da dieser Parameter eine Variante ist, freigegeben deaktivieren die Variante Ressourcen.  
  
 In Fällen, in denen Befehle innerhalb eines Fensters Hierarchie arbeiten müssen, das <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle muss verwendet werden. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle verfügt über eine ähnliche Vertrag mit ähnlichen Methoden: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Elemente der Benutzeroberfläche hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementation (Implementierung)](../../extensibility/internals/command-implementation.md)