---
title: "COM Interop Wrapper Error | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyassembly"
  - "Vs.refruntlbimp"
helpviewer_keywords: 
  - "COM Interop Wrapper dialog box"
ms.assetid: 9a9d6374-ee26-4dbc-9e34-e1d90f6254b4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop Wrapper Error
Dieses Meldungsfeld wird angezeigt, wenn das Projektsystem einen COM\-Interop\-Wrapper für eine bestimmte Komponente nicht erstellen konnte.  COM\-Interop\-Wrapper werden von der Common Language Runtime \(CLR\) angefordert, um COM\-Komponenten zu verwalten und mit diesen zu kommunizieren.  Weitere Informationen finden Sie unter [COM\-Interoperabilität in Visual Basic und Visual C\#](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).  
  
 Häufige Ursachen für diesen Fehler sind:  
  
-   Die Typbibliothek für die Komponente ist nicht ordnungsgemäß registriert.  
  
-   Eine Komponente, von der die umschlossene Komponente abhängig ist, konnte nicht auf Ihrem Computer gefunden werden.  
  
 In beiden Fällen müssen Sie sicherstellen, dass die COM\-Komponente auf dem Computer ordnungsgemäß installiert und registriert ist und den Vorgang wiederholen.  
  
> [!TIP]
>  Einen für Ihre spezifische COM\-Komponente veröffentlichten COM\-Interop\-Wrapper finden Sie auch auf der [MSDN\-Website](http://go.microsoft.com/fwlink/?LinkId=3355).  
  
> [!NOTE]
>  COM\-Interop\-Wrapper werden manchmal als „primäre Interop\-Assemblys“ bezeichnet. Diese Begriffe stellen Synonyme dar.  
  
## Siehe auch  
 [Komponentenmodell\-Namespaces in Visual Studio](http://msdn.microsoft.com/de-de/705d0add-0707-44ba-a6de-637381d9c937)   
 [Component Authoring](../Topic/Component%20Authoring.md)   
 [COM Interop](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md)   
 [COM Interoperability in .NET Framework Applications](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)