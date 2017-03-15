---
title: "Gewusst wie: Festlegen einer Sicherheitszone f&#252;r eine ClickOnce-Anwendung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce-Bereitstellung, Sicherheitseinstellungen"
  - "Codezugriffssicherheit, ClickOnce-Anwendungen"
  - "Sicherheitszonen, ClickOnce-Anwendungen"
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# Gewusst wie: Festlegen einer Sicherheitszone f&#252;r eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Festlegen von Codezugriffssicherheits\-Berechtigungen für eine ClickOnce\-Anwendung müssen Sie mit einem Basissatz von Berechtigungen auf der Seite **Sicherheit** des **Projekt\-Designer** beginnen.  
  
 In den meisten Fällen können Sie auch die Zone **Internet** mit einem begrenzten Satz von Berechtigungen oder die Zone **Lokales Intranet** mit einem umfangreicheren Satz von Berechtigungen wählen. Wenn die Anwendung benutzerdefinierte Berechtigungen erfordert, können Sie die Sicherheitszone **Benutzerdefiniert** wählen. Weitere Informationen zum Einstellen von Berechtigungen finden Sie unter [Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce\-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### Festlegen eine Sicherheitszone  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen\-Explorer** im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Sicherheit**.  
  
3.  Aktivieren Sie das Kontrollkästchen **ClickOnce\-Sicherheitseinstellungen aktivieren**.  
  
4.  Wählen Sie das Optionsfeld **Teilweise vertrauenswürdige Anwendung** aus.  
  
     Die Steuerelemente im Abschnitt **ClickOnce\-Sicherheitsberechtigungen** sind aktiviert.  
  
5.  Wählen Sie aus der Dropdownliste **Zone, aus der die Anwendung installiert wird** eine Sicherheitszone.  
  
## Siehe auch  
 [Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce\-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Codezugriffssicherheit für ClickOnce\-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)