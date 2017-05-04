---
title: "Gewusst wie: Signieren von Office-Projektmappen | Microsoft Docs"
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
  - "Zertifikate [Office-Entwicklung in Visual Studio], Office-Projektmappen"
  - "Sicherheit [Office-Entwicklung in Visual Studio], Signieren von Office-Projektmappen"
  - "Signieren von Manifesten [Office-Entwicklung in Visual Studio]"
ms.assetid: d3df5ee6-f1b7-47ed-b7ee-8985679ee3af
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Gewusst wie: Signieren von Office-Projektmappen
  Wenn Sie eine Projektmappe signieren, können Sie der Projektmappe mithilfe des Zertifikats Vertrauenswürdigkeit gewähren.  Sie können ein Zertifikat für mehrere Projektmappen verwenden, und alle Projektmappen werden ohne zusätzliche Aktualisierungen der Sicherheitsrichtlinie als vertrauenswürdig eingestuft.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Wenn Sie Anwendungs\- und Bereitstellungsmanifeste mit dem Tool zum Generieren und Bearbeiten von Manifesten \(mage.exe und mageui.exe\) manuell bearbeiten, müssen Sie die Manifeste erneut signieren, bevor Sie sie verwenden können.  Weitere Informationen finden Sie unter [How to: Re-sign Application and Deployment Manifests](../Topic/How%20to:%20Re-sign%20Application%20and%20Deployment%20Manifests.md).  
  
## Signieren mithilfe eines Zertifikats  
 Ein Zertifikat ist eine Datei, die einen eindeutigen Schlüssel und die Identität des Projektmappenherausgebers enthält.  Sie können Zertifikate bei einer Zertifizierungsstelle erwerben oder Ihr eigenes Zertifikat erstellen, welches Sie von einer Zertifizierungsstelle signieren lassen.  
  
 Visual Studio signiert Office\-Projektmappen mit einem temporären Zertifikat, um das Debuggen zu ermöglichen.  Sie sollten das temporäre Zertifikat nicht als Beweis in bereitgestellten Projektmappen verwenden.  
  
#### So signieren Sie eine Office\-Projektmappe mithilfe eines Zertifikats  
  
1.  Klicken Sie im Menü **Projekt** auf *SolutionName***\-Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Signierung**.  
  
3.  Wählen Sie **ClickOnce\-Manifeste signieren** aus.  
  
4.  Suchen Sie das Zertifikat, indem Sie auf **Aus Speicher auswählen** oder **Aus Datei wählen** klicken und zum Zertifikat navigieren.  
  
5.  Um zu überprüfen, ob das richtige Zertifikat verwendet wird, klicken Sie auf **Weitere Details**, um die Zertifikatsinformationen anzuzeigen.  
  
## Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md)   
 [Seite "Signierung", Projekt-Designer](../ide/reference/signing-page-project-designer.md)  
  
  