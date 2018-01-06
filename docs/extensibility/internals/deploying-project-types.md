---
title: Bereitstellen von Projekttypen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2171a940951d828df358d09dae5fec68b6475e4d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-project-types"></a>Bereitstellen von Projekttypen
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]installiert einen neuen Projekttyp Aggregator (ProjectAggregator2.dll) und auch ein Windows Installer-Paket für die Verteilung (ProjectAggregator2.msi). Sie müssen den neuen Aggregator für Projekttypen von verwaltetem Code verwenden. ProjectAggregator2 funktioniert Scanning Einschränkungen in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt Aggregator, die Projekttypen von verwaltetem Code zu verhindern, dass nicht mehr ordnungsgemäß funktionieren. Die folgenden Schritte beschreiben, wie so ändern Sie das VSPackage, um den neuen Aggregator zu verwenden.  
  
1.  Entfernen Sie das Projekt NativeHierarchyWrapper aus der Projektmappe.  
  
2.  Entfernen Sie alle Binärdateien NativeHierarchyWrapper aus Ihr Setup.  
  
3.  Fügen Sie mit dem Setup ProjectAggregator2.msi hinzu.