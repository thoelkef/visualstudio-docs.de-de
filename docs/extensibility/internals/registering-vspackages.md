---
title: "Registrieren von VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "verwaltete VSPackages, registrieren"
  - "verwaltete VSPackages-Registrierung"
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Registrieren von VSPackages
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] beruht auf .pkgdef\-Dateien, um VSPackages zu beschreiben und zu suchen.  Eine PKGDEF\-Datei enthält alle Registrierungsinformationen, die andernfalls in die Systemregistrierung hinzugefügt werden.  Verwaltetes VSPackages werden registriert, indem Attribute auf den Quellcode hinzufügt und dann auf [CreatePkgDef\-Dienstprogramm](../../extensibility/internals/createpkgdef-utility.md) der resultierenden Assembly ausgeführt wird, um eine PKGDEF\-Datei zu generieren.  
  
## In diesem Abschnitt  
 [Angabe des VSPackage Dateispeicherorts für die VS\-Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Beschreibt den Pfad zur Laden von VSPackages.  
  
 [Registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Erklärt, wie ein VSPackage registriert.  
  
 [Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Beschreibt, wie ein Registrierungsdaten manifest erstellt, die verwendet werden kann, um verwaltete VSPackages bereitzustellen.