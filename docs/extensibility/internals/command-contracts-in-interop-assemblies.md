---
title: "Befehl Vertr&#228;ge in Interop-Assemblys | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehlsbehandlung mit Interop-Assemblys, Befehl Verträge"
  - "Interop-Assemblys, Verträge, Befehl"
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Befehl Vertr&#228;ge in Interop-Assemblys
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Basisvertrag für die Behandlung von Befehlen, die über die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle ist, dass die Umgebung Ruft die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, um zu bestimmen, ob der Befehl unterstützt wird und, falls es unterstützt wird, um den Status und den Text festzulegen. Dann die Umgebung Ruft die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode zum Ausführen des Befehls.  
  
 Die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode ist für alle Befehle identisch behandelt. Weitere Kommunikation bei Bedarf \(z. B. mit Dropdown\-Listen\) erfolgt durch Aufrufen der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> \-Methode mit entsprechenden Parametern. Die Interpretation dieser Parameter hängt von den angegebenen Befehl ab.  
  
 Wenn das Ziel des Befehls Werte im Ausgabeparameter zurückgibt, ist der Aufrufer immer verantwortlich für das Freigeben von Ressourcen, die zugeordnet war. Da dieser Parameter eine Variante ist, deaktivieren die Variante gibt die Ressourcen frei.  
  
 In Fällen, in denen Befehle in einem Hierarchiefenster verwenden müssen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle verwendet werden muss. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle verfügt über eine ähnliche Vertrag mit ähnlichen Methoden: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementierung](../../extensibility/internals/command-implementation.md)