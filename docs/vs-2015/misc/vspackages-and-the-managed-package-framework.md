---
title: VSPackages und das Managed Package Framework | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: 41eb5cc816616ca2d99b68eb73fedbd527778274
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511105"
---
# <a name="vspackages-and-the-managed-package-framework"></a>VSPackages und das Managed Package Framework
Sie können die Entwicklungszeit reduzieren, indem Sie erstellen eine VSPackage mit dem verwalteten Paket Framework (MPF)-Klassen anstelle von mithilfe von COM-Interop-Klassen.  
  
 Es gibt zwei Möglichkeiten, ein verwaltetes VSPackage zu erstellen:  
  
-   Verwenden der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Paket-Projektvorlage  
  
     Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Menü-Befehl mit der Visual Studio-Paketvorlage](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
-   Erstellen Sie Ihr VSPackage ohne die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Paket-Projektvorlage  
  
     Sie können z. B. Kopieren Sie ein Beispiel für VSPackage und die GUIDs und die Namen ändern. Beispiele finden Sie im Abschnitt VSX [Code Gallery](http://code.msdn.microsoft.com/vsx/).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Managed Package Framework-Klassen](../misc/managed-package-framework-classes.md)  
 Beschreibt und führt die Klasse MPF-Namespaces und die DLL-Dateien.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Exemplarische Vorgehensweise: Erstellen eines Menübefehls mithilfe der Visual Studio-Paketvorlage](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Erläutert, wie ein verwaltetes VSPackage zu erstellen.  
  
 [Verwaltete VSPackages](../misc/managed-vspackages.md)  
 Führt die Aspekte des VSPackages, die an verwalteten Code gelten.