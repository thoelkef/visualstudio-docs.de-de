---
title: Bereitstellen von Projekttypen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12af8607dd1561a4a2561cc688d2bb4ba0f07c88
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-project-types"></a>Bereitstellen von Projekttypen
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] installiert einen neuen Projekttyp Aggregator (ProjectAggregator2.dll) und auch ein Windows Installer-Paket für die Verteilung (ProjectAggregator2.msi). Sie müssen den neuen Aggregator für Projekttypen von verwaltetem Code verwenden. ProjectAggregator2 funktioniert Scanning Einschränkungen in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt Aggregator, die Projekttypen von verwaltetem Code zu verhindern, dass nicht mehr ordnungsgemäß funktionieren. Die folgenden Schritte beschreiben, wie so ändern Sie das VSPackage, um den neuen Aggregator zu verwenden.  
  
1.  Entfernen Sie das Projekt NativeHierarchyWrapper aus der Projektmappe.  
  
2.  Entfernen Sie alle Binärdateien NativeHierarchyWrapper aus Ihr Setup.  
  
3.  Fügen Sie mit dem Setup ProjectAggregator2.msi hinzu.