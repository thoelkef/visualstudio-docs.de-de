---
title: "Vorgehensweise: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 86dbdf312c1356c6fb63fcfa32f1dd362b4c7599
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Gewusst wie: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung
Beim Festlegen von Codezugriffssicherheits-Berechtigungen für eine ClickOnce-Anwendung müssen Sie mit einem Basissatz von Berechtigungen auf der Seite **Sicherheit** des **Projekt-Designer**beginnen.  
  
 In den meisten Fällen können Sie auch die Zone **Internet** mit einem begrenzten Satz von Berechtigungen oder die Zone **Lokales Intranet** mit einem umfangreicheren Satz von Berechtigungen wählen. Wenn die Anwendung benutzerdefinierte Berechtigungen erfordert, können Sie die Sicherheitszone **Benutzerdefiniert** wählen. Weitere Informationen zum Einstellen von Berechtigungen finden Sie unter [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Festlegen eine Sicherheitszone  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Sicherheit** .  
  
3.  Aktivieren Sie das Kontrollkästchen **ClickOnce-Sicherheitseinstellungen aktivieren** .  
  
4.  Wählen Sie das Optionsfeld **Teilweise vertrauenswürdige Anwendung** aus.  
  
     Die Steuerelemente im Abschnitt **ClickOnce-Sicherheitsberechtigungen** sind aktiviert.  
  
5.  Wählen Sie aus der Dropdownliste **Zone, aus der die Anwendung installiert wird** eine Sicherheitszone.  
  
## <a name="see-also"></a>Siehe auch  
 [How to: Set Custom Permissions for a ClickOnce Application (Vorgehensweise: Festlegen von benutzerdefinierten Berechtigungen für eine ClickOnce-Anwendung)](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)