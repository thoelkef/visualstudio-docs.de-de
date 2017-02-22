---
title: "Gewusst wie: Festlegen benutzerdefinierter Berechtigungen f&#252;r eine ClickOnce-Anwendung | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
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
  - "ClickOnce-Anwendungen, Berechtigungen"
  - "Berechtigungen, ClickOnce-Anwendungen"
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Festlegen benutzerdefinierter Berechtigungen f&#252;r eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung bereitstellen, die Standardberechtigungen für die Zonen „Internet“ oder „Lokales Intranet“ verwendet. Alternativ können Sie eine benutzerdefinierte Zone für die spezifischen Berechtigungen erstellen, die die Anwendung benötigt. Diese Berechtigungen können Sie erstellen, indem Sie die Sicherheitsberechtigungen auf der Seite **Sicherheit** des **Projekt\-Designers** anpassen.  
  
### So passen Sie eine Berechtigung an  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen\-Explorer** im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Sicherheit**.  
  
3.  Aktivieren Sie das Kontrollkästchen **ClickOnce\-Sicherheitseinstellungen aktivieren**.  
  
4.  Wählen Sie das Optionsfeld **Teilweise vertrauenswürdige Anwendung** aus.  
  
     Die Steuerelemente im Abschnitt **ClickOnce\-Sicherheitsberechtigungen** sind aktiviert.  
  
5.  Klicken Sie in der Dropdownliste **Zone, aus der die Anwendung installiert wird** auf **\(Benutzerdefiniert\)**.  
  
6.  Klicken Sie auf **Berechtigungs\-XML bearbeiten**.  
  
     Die Datei „app.manifest“ wird im XML\-Editor geöffnet.  
  
7.  Fügen Sie vor dem `</applicationRequestMinimum>`\-Element den XML\-Code für Berechtigungen hinzu, den Ihre Anwendung benötigt.  
  
    > [!NOTE]
    >  Sie können die `ToXml`\-Methode einer Berechtigung verwenden, die zum Generieren des XML\-Codes für das Anwendungsmanifest festgelegt wurde. Rufen Sie z.B. zum Generieren des XML\-Codes für die <xref:System.Security.Permissions.EnvironmentPermission>\-Berechtigung die <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A>\-Methode auf. Weitere Informationen zur Struktur der Berechtigung, die für XML festgelegt ist, finden Sie unter [NIB: Vorgehensweise: Importieren eines Berechtigungssatzes mithilfe einer XML\-Datei](http://msdn.microsoft.com/de-de/dea16b54-c108-408a-ac36-cdc05f746236).  
  
## Siehe auch  
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Codezugriffssicherheit für ClickOnce\-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)