---
title: Befehle und Menüs, die Interop-Assemblys verwenden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d050f2e96eb78462f9e5e77504a365d17ed01d6d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509243"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Befehle und Menüs, die Interop-Assemblys verwenden
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Befehle und Menüs, dass verwenden Interop-Assemblys](https://docs.microsoft.com/visualstudio/extensibility/internals/commands-and-menus-that-use-interop-assemblies).  
  
Eine VSPackage, die Menü-und Symbolleistenbefehle implementiert werden, mithilfe von Interop-Assemblys muss Schritte ausführen:  
  
-   Informieren Sie die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE) über die unterstützten Befehle und gibt an, ob sie derzeit aktiviert sind.  
  
-   Beachten Sie die Regeln, (Vertrag) für die Behandlung von Befehlen.  
  
-   Befehlsbehandlung explizit implementieren, indem Sie entweder die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle.  
  
 Im folgenden wird beschrieben, wie Sie diese Aufgaben durchführen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Bestimmen des Befehlsstatus mithilfe von Interop-Assemblys](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Beschreibt, wie eine VSPackage für die IDE benachrichtigt dazu, welche Befehle sie unterstützt und gibt an, ob sie derzeit aktiviert sind.  
  
 [Befehlsverträge in Interop-Assemblys](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Stellt eine Definition des Vertrags einfachen Befehl ein, die allen VSPackages Implementieren von Befehlen, die mithilfe von Interopassemblys  
  
 [Implementation (Implementierung)](../../extensibility/internals/command-implementation.md)  
 Bietet einen Überblick darüber, wie eine VSPackage einen Befehl implementiert.  
  
 [Registrieren der Befehlshandler von Interop-Assemblys](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Beschreibt die Registrierungseinträge erforderlich, um der IDE benachrichtigt, dass eine VSPackage einen Befehlshandler bereitstellt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Verfügbarkeit](../../extensibility/internals/command-availability.md)  
 Beschreibt die Kriterien, die von der IDE verwendet werden, um zu bestimmen, welche VSPackage-Befehle verfügbar sind und welches Objekt sie verarbeitet.  
  
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Enthält Details dazu, wie Sie eine Benutzeroberfläche erstellen, verwendet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Befehl unterstützen.  
  
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Eine Übersicht über den Prozess verwendet, um ein Objekt mit den richtigen befehlsanforderung verknüpfen.

