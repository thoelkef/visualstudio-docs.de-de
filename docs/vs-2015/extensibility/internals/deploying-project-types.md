---
title: Bereitstellen von Projekttypen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fda84d5f7467a65b254d3b12b0466b6ab415d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196877"
---
# <a name="deploying-project-types"></a>Bereitstellen von Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] installiert einen neuen Projekttyp Aggregator (ProjectAggregator2.dll) und auch ein Windows Installer Paket für die Weiterverteilung (ProjectAggregator2.msi). Sie müssen den neuen Aggregator für Projekttypen mit verwaltetem Code verwenden. ProjectAggregator2 Works weist Einschränkungen im [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektaggregator auf, die verhindern, dass Projekttypen mit verwaltetem Code ordnungsgemäß funktionieren. In den folgenden Schritten wird beschrieben, wie Sie Ihr VSPackage für die Verwendung des neuen Aggregators ändern.  
  
1. Entfernen Sie das nativehierarchywrapper-Projekt aus der Projekt Mappe.  
  
2. Entfernen Sie alle nativehierarchywrapper-Binärdateien aus dem Setup.  
  
3. Fügen Sie dem Setup ProjectAggregator2.msi hinzu.
