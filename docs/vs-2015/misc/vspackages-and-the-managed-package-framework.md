---
title: VSPackages und das Managed Package Framework | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 84fb41bfc80415535ca41d6b1a8c9dcf47124c7a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298238"
---
# <a name="vspackages-and-the-managed-package-framework"></a>VSPackages und das Managed Package Framework
Sie können die Entwicklungszeit verringern, indem Sie ein VSPackage mit den MPF-Klassen (Managed Package Framework) anstatt mithilfe von COM-Interop-Klassen erstellen.  
  
 Es gibt zwei Möglichkeiten, ein verwaltetes VSPackage zu erstellen:  
  
- Verwenden der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Paket Projektvorlage  
  
     Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Menübefehls mithilfe der Visual Studio-Paket Vorlage](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
- Erstellen des VSPackages ohne die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Paket Projektvorlage  
  
     Beispielsweise können Sie ein Beispiel-VSPackage kopieren und die GUIDs und die Namen ändern. 
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Managed Package Framework-Klassen](../misc/managed-package-framework-classes.md)  
 Beschreibt die MPF-Klassen-Namespaces und dll-Dateien und listet diese auf.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Exemplarische Vorgehensweise: Erstellen eines Menübefehls mithilfe der Visual Studio-Paketvorlage](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Erläutert, wie ein verwaltetes VSPackage erstellt wird.  
  
 [Verwaltete VSPackages](../misc/managed-vspackages.md)  
 Führt Aspekte von VSPackages ein, die auf verwalteten Code angewendet werden.