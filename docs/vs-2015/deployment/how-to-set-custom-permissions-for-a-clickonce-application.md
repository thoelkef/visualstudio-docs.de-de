---
title: 'Vorgehensweise: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6739f38e91ce998441c4cfa62453d485a5d370e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697550"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung bereitstellen, die Standardberechtigungen für die Zonen „Internet“ oder „Lokales Intranet“ verwendet. Alternativ können Sie eine benutzerdefinierte Zone für die spezifischen Berechtigungen erstellen, die die Anwendung benötigt. Diese Berechtigungen können Sie erstellen, indem Sie die Sicherheitsberechtigungen auf der Seite **Sicherheit** des **Projekt-Designers**anpassen.  
  
### <a name="to-customize-a-permission"></a>So passen Sie eine Berechtigung an  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Sicherheit** .  
  
3. Aktivieren Sie das Kontrollkästchen **ClickOnce-Sicherheitseinstellungen aktivieren** .  
  
4. Wählen Sie das Optionsfeld **Teilweise vertrauenswürdige Anwendung** aus.  
  
     Die Steuerelemente im Abschnitt **ClickOnce-Sicherheitsberechtigungen** sind aktiviert.  
  
5. Klicken Sie in der Dropdownliste **Zone, aus der die Anwendung installiert wird** auf **(Benutzerdefiniert)**.  
  
6. Klicken Sie auf **Berechtigungs-XML bearbeiten**.  
  
     Die Datei „app.manifest“ wird im XML-Editor geöffnet.  
  
7. Fügen Sie vor dem `</applicationRequestMinimum>` -Element den XML-Code für Berechtigungen hinzu, den Ihre Anwendung benötigt.  
  
    > [!NOTE]
    > Sie können die `ToXml` -Methode einer Berechtigung verwenden, die zum Generieren des XML-Codes für das Anwendungsmanifest festgelegt wurde. Rufen Sie z.B. zum Generieren des XML-Codes für die <xref:System.Security.Permissions.EnvironmentPermission> -Berechtigung die <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> -Methode auf. Weitere Informationen zur Struktur der Berechtigung, die für XML festgelegt ist, finden Sie unter [NIB: Vorgehensweise: Importieren eines Berechtigungssatzes mithilfe einer XML-Datei](https://msdn.microsoft.com/dea16b54-c108-408a-ac36-cdc05f746236).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Code Zugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
