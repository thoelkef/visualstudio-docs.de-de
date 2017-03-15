---
title: "Komponenten des Redistributable-Pakets | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Komponenten des Redistributable-Pakets"
  - "Installation [Visual Studio SDK], Komponenten des Redistributable-Pakets"
ms.assetid: 5072281f-3cb3-4985-bd93-c7981233bf92
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Komponenten des Redistributable-Pakets
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] enthält Code, den Sie an die Benutzer nach den Lizenzvertrag von Ausdrücken [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK verteilen können.  Solche verteilbaren Komponenten zählen Pakete und Mergemodule, die Teil des Installationsvorgangs des Produkts zu kommunizieren, und Quellcode von Windows Installer, den Sie in der VSPackages kompilieren.  
  
 Die folgende Tabelle beschreibt die verteilbaren Komponenten, die im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK enthalten sind.  Die Komponenten können in  *Pfad SDK\-Installations Visual Studio*\\ \\. \\ VisualStudioIntegration Redistributables gefunden werden.  
  
|Dateiname|Beschreibung|  
|---------------|------------------|  
|VSSDKTestHost.exe|Sie können diese ausführbare Datei im Rahmen der Installation installieren.|  
  
## Verteilbare Pakete installieren  
 Verteilbare Komponenten installieren, werden als ausführbare Code bereitgestellt von Windows Installer\-Paketen \(MSI\-Dateien\), sodass Microsoft Updates bereitstellen kann, wenn dies erforderlich ist, Sicherheitslücken oder andere kritische Fehler zu beheben.  
  
 Da Windows Installer darf, dass nur jeweils ein Paket installiert, erfordert das Einrichten eines verteilbaren Pakets, dass Sie ein separates ausführbares Programm, das mehrere Pakete nacheinander installiert.  Ein solches Programm wird häufig ein *Chainer* oder einem *Bootstrapper*bezeichnet.  
  
> [!IMPORTANT]
>  *Geschachtelte Installation* \(auch als *parallele Installation*in Windows Installer\) wird abgeraten, da ein geschachteltes“ Produkt „nicht unabhängig voneinander geändert werden kann.  Sie kann nur durch das Produkt gepatcht werden, die es installiert hat.  Da die verteilbaren Pakete [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] Dateien zu den freigegebenen Verzeichnissen installieren und die unabhängige Patchen unterstützen müssen, dürfen sie nicht installiert werden, indem eine geschachtelte Installation verwenden.  
  
## Siehe auch  
 [Freigeben eines Produkts](../misc/releasing-a-visual-studio-integration-product.md)