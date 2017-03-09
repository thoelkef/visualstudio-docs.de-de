---
title: "MSBuild Error MSB3152 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
helpviewer_keywords: 
  - "MSB3152"
ms.assetid: 5a3859d4-4107-4e46-bb42-04de92b551de
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3152
**Der Installationspfad für die erforderlichen Komponenten wurde nicht auf "Webseite für Bereitstellung der Komponenten" festgelegt, und die Datei \<Datei\> in Element \<Paket\> konnte auf dem Datenträger nicht gefunden werden.  Weitere Informationen finden Sie in der Hilfe.**  
  
 Dieser Fehler tritt auf, wenn eine für das erforderliche Installationsprogramm benötigte Datei fehlt.  Die Installationsprogrammdateien werden von Visual Studio in einem speziellen Ordner für verteilbare Pakete abgelegt.  Der Ordner ist abhängig von der Version von Visual Studio, die für die Entwicklung verwendet wird.  Weitere Informationen zum Speicherort des speziellen Ordners finden Sie unter [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md).  
  
### So beheben Sie diesen Fehler  
  
-   Ermitteln Sie, ob die Datei auf Datenträger vorhanden ist.  
  
-   Versuchen Sie, das Paketproblem mithilfe von HomeSite zu beheben.  
  
-   Legen Sie in der Projektdatei `CopyComponents` auf `false` fest.  
  
-   Verwenden Sie das fehlerhafte Bootstrapperpaket nicht.  
  
## Siehe auch  
 [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md)