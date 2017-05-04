---
title: "Bereitstellen einer Office-Projektmappe | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ClickOnce-Bereitstellung [Office-Entwicklung in Visual Studio], Informationen zur Bereitstellung von ClickOnce-Projektmappen"
  - "ClickOnce-Bereitstellung [Office-Entwicklung in Visual Studio], Ereignisanzeige"
  - "ClickOnce-Bereitstellung [Office-Entwicklung in Visual Studio], Problembehandlung"
  - "Bereitstellen von Anwendungen [Office-Entwicklung in Visual Studio], Ereignisanzeige"
  - "Bereitstellen von Anwendungen [Office-Entwicklung in Visual Studio], Office-Projektmappen (2007 System)"
  - "Bereitstellen von Anwendungen [Office-Entwicklung in Visual Studio], Problembehandlung"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Bereitstellen von Office-Projektmappen"
  - "Office-Entwicklung in Visual Studio, Bereitstellen von Office-Projektmappen"
  - "Office-Entwicklung in Visual Studio, Ereignisanzeige"
  - "Office-Entwicklung in Visual Studio, Problembehandlung"
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio], Bereitstellen"
  - "Projektmappen [Office-Entwicklung in Visual Studio], Bereitstellen von Office-Projektmappen (2007 System)"
ms.assetid: 4cdf4bc6-72c5-4166-8019-d5fd61281079
caps.latest.revision: 78
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# Bereitstellen einer Office-Projektmappe
  Sie können Office\-Lösungen mit ClickOnce oder Windows Installer bereitstellen.  Mit ClickOnce verringern Sie die Anzahl von Schritten, die zum Bereitstellen und Aktualisieren der Lösung erforderlich sind.  Wenn Sie Windows Installer verwenden, haben Sie die Kontrolle darüber, wie eine Lösung installiert wird und welche Informationen das Setupprogramm anzeigt, wenn der Benutzer die Lösung installiert.  
  
## Bereitstellen einer Lösung mit ClickOnce  
 Wenn Sie eine Lösung mit ClickOnce bereitstellen, veröffentlichen Sie diese an einem zentralen Speicherort, wo Benutzer sie installieren und ausführen können.  Sie können die Lösung aktualisieren, ohne an die Benutzer ein neues Setupprogramm verteilen zu müssen.  Diese Bereitstellungsoption ist einfacher, aber Sie können dem Benutzer bei der Installation keine speziellen Informationsseiten anzeigen.  Außerdem müssen Lösungen mehrmals installiert werden, wenn auf dem Computer mehrere Benutzer eingerichtet sind.  Siehe [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Bereitstellen einer Lösung mit Windows Installer  
 Wenn Sie eine Lösung mit Windows Installer bereitstellen, verteilen Sie ein Setupprogramm an Benutzer, und diese installieren die Lösung, indem sie das Setupprogramm verwenden.  Das Setupprogramm kann eine Lösung sowohl einzeln für den aktuellen Benutzer als auch gleichzeitig für alle Benutzer eines Computers installieren.  Sie haben auch etwas mehr Kontrolle über die Optionen, die für Benutzer bei der Installation angezeigt werden.  Beispielsweise können Sie eine Lizenzvereinbarung anzeigen oder es dem Benutzer ermöglichen, bestimmte Komponenten einer Lösung zu installieren.  Wenn Sie die Lösung aktualisieren, müssen Sie ein neues Setupprogramm verteilen.  Siehe [Bereitstellen einer Office-Lösung mithilfe von Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Bereitstellen einer Office-Lösung mithilfe von Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Problembehandlung bei der Office-Projektmappenbereitstellung](../vsto/troubleshooting-office-solution-deployment.md)  
  
  