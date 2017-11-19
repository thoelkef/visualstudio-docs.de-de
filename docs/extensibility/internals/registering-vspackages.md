---
title: Registrierung von VSPackages | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d580d3d74d8648b7181ac1ca384d3232fa8225b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="registering-vspackages"></a>Registrierung von VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]basiert auf der PKGDEF-Dateien, um zu beschreiben, und suchen Sie eine VSPackage. Eine PKGDEF-Datei enthält alle Registrierungsinformationen, die andernfalls in der systemregistrierung hinzugefügt werden würde. Verwaltete VSPackages registriert sind, indem Attribute auf den Quellcode hinzufügen und dann die [CreatePkgDef Utility](../../extensibility/internals/createpkgdef-utility.md) für die resultierende Assembly eine PKGDEF-Datei zu generieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Angeben des VSPackage-Dateispeicherorts für die VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Beschreibt den Pfad zum Laden für VSPackages.  
  
 [Registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Erläutert, wie eine VSPackage registriert.  
