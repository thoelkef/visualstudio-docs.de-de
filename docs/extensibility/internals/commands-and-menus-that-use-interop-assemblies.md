---
title: "Befehle und Menüs, die mithilfe von Interop-Assemblys | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee9fa1faa52afb2ea6d8154b4767fcab2cee0981
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Befehle und Menüs, die mithilfe von Interop-Assemblys
Eine VSPackage, die Menü-und implementiert werden, mithilfe von Interop-Assemblys muss:  
  
-   Informieren der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) zu den Befehlen, die es unterstützt und gibt an, ob sie derzeit aktiviert sind.  
  
-   Unterliegen Sie den Regeln (Vertrag) für die Behandlung von Befehlen.  
  
-   Befehlsbehandlung explizit zu implementieren, indem Sie entweder die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle.  
  
 Im folgenden wird beschrieben, wie folgende Aufgaben ausgeführt werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Bestimmen des Befehlsstatus mithilfe von Interop-Assemblys](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Beschreibt, wie eine VSPackage die IDE benachrichtigt über welche Befehle unterstützt und gibt an, ob sie derzeit aktiviert sind.  
  
 [Befehlsverträge in Interop-Assemblys](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Stellt eine Definition des Vertrags grundlegende Befehl verwendet von allen VSPackages Implementieren von Befehlen, die mithilfe von Interopassemblys  
  
 [Implementation (Implementierung)](../../extensibility/internals/command-implementation.md)  
 Bietet einen Überblick darüber, wie eine VSPackage einen Befehl implementiert.  
  
 [Registrieren der Befehlshandler von Interop-Assemblys](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Beschreibt die Registrierungseinträge erforderlich, um der IDE benachrichtigt, dass eine VSPackage Befehlshandler bereitstellt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Verfügbarkeit](../../extensibility/internals/command-availability.md)  
 Beschreibt die Kriterien, die von der IDE verwendet werden, um zu bestimmen, welche Befehle VSPackage verfügbar sind und welche Ziehpunkte.  
  
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Enthält Details dazu, wie Sie eine Benutzeroberfläche erstellen, verwendet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Befehl unterstützen.  
  
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Eine Übersicht über den Prozess verwendet, um ein Objekt mit den richtigen befehlsanforderung verknüpfen.