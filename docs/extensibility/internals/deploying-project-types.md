---
title: "Bereitstellen von Projekttypen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekte [Visual Studio SDK] verwaltetem code"
  - "Projekte [Visual Studio SDK], aggregator"
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Bereitstellen von Projekttypen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] installiert einen neuen Projekttyp\-Aggregator \(ProjectAggregator2.dll\) und auch die Windows Installer\-Paket für die Verteilung \(ProjectAggregator2.msi\). Sie müssen den neuen Aggregator für Typen von verwaltetem Code verwenden. ProjectAggregator2 funktioniert Scanning Einschränkungen in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt Aggregator, die verhindern, dass Projekttypen von verwaltetem Code ordnungsgemäß funktioniert. Die folgenden Schritte beschreiben, wie Sie Ihr VSPackage Verwendung den neuen Aggregator ändern.  
  
1.  Entfernen Sie das NativeHierarchyWrapper\-Projekt aus der Projektmappe.  
  
2.  Entfernen Sie Binärdateien NativeHierarchyWrapper aus Ihr Setup.  
  
3.  Fügen Sie ProjectAggregator2.msi auf Ihr Setup.