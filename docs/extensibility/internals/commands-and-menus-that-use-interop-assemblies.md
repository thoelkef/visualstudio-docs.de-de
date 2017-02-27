---
title: "Befehle und Men&#252;s, die mithilfe von Interop-Assemblys | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Menüs, Verwendung von Interop-Assemblys"
  - "Interop-Assemblys, die mithilfe von Befehlen und Menüs"
  - "Befehle, die Behandlung von mithilfe von Interop-Assemblys"
  - "Befehlsbehandlung mit Interop-Assemblys"
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Befehle und Men&#252;s, die mithilfe von Interop-Assemblys
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein VSPackage, die Menü\-und Symbolleistenbefehle implementiert, mithilfe von Interop\-Assemblys muss:  
  
-   Informiert den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) über die unterstützten Befehle und gibt an, ob sie derzeit aktiviert sind.  
  
-   Die Regeln \(Vertrag\) für die Behandlung von Befehlen entsprechen.  
  
-   Befehlsbehandlung explizit zu implementieren, indem Sie entweder die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle.  
  
 Im folgenden wird beschrieben, wie folgende Aufgaben ausgeführt werden.  
  
## In diesem Abschnitt  
 [Bestimmen des Status des Befehls mithilfe von Interop\-Assemblys](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Beschreibt, wie ein VSPackage die IDE benachrichtigt unterstützt über die Befehle und gibt an, ob sie derzeit aktiviert sind.  
  
 [Befehl Verträge in Interop\-Assemblys](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Stellt eine Definition des Vertrags einfachen Befehl werden alle VSPackages Implementieren von Befehlen mithilfe von Interop\-Assemblys  
  
 [Implementierung](../../extensibility/internals/command-implementation.md)  
 Bietet einen Überblick darüber, wie ein VSPackage einen Befehl implementiert.  
  
 [Registrierung der Befehlshandler Interop\-Assembly](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Beschreibt der IDE benachrichtigt, dass ein VSPackage einen Befehlshandler bietet erforderlichen Registrierungseinträge.  
  
## Verwandte Abschnitte  
 [Verfügbarkeit](../../extensibility/internals/command-availability.md)  
 Beschreibt die Kriterien, die von der IDE verwendet werden, um zu bestimmen, welche VSPackage\-Befehle verfügbar sind und welches Objekt sie behandelt.  
  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Ausführliche Informationen dazu, wie Sie eine Benutzeroberfläche erstellen, verwendet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Befehl unterstützen.  
  
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Eine Übersicht über den Prozess verwendet, um ein Objekt mit den richtigen befehlsanforderung verknüpfen.