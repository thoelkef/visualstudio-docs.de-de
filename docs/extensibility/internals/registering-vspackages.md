---
title: Registrierung von VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6f7e603fbc023415ad2b8ddc157f239feb53768
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="registering-vspackages"></a>Registrierung von VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] basiert auf der PKGDEF-Dateien, um zu beschreiben, und suchen Sie eine VSPackage. Eine PKGDEF-Datei enthält alle Registrierungsinformationen, die andernfalls in der systemregistrierung hinzugefügt werden würde. Verwaltete VSPackages registriert sind, indem Attribute auf den Quellcode hinzufügen und dann die [CreatePkgDef Utility](../../extensibility/internals/createpkgdef-utility.md) für die resultierende Assembly eine PKGDEF-Datei zu generieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Angeben des VSPackage-Dateispeicherorts für die VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Beschreibt den Pfad zum Laden für VSPackages.  
  
 [Registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Erläutert, wie eine VSPackage registriert.  
