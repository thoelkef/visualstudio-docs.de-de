---
title: "Erforderliche &#196;nderungen zum Ausf&#252;hren von Office-Projekten, die zu .NET Framework&#160;4 oder .NET Framework 4.5 migriert werden | Microsoft Docs"
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
  - "Office-Projekte [Office-Entwicklung in Visual Studio], Migrieren auf .NET Framework 4"
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Erforderliche &#196;nderungen zum Ausf&#252;hren von Office-Projekten, die zu .NET Framework&#160;4 oder .NET Framework 4.5 migriert werden
  Wenn das Zielframework eines Office\-Projekts aus einer früheren Version von .NET Framework in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie die folgenden Aufgaben ausführen, um sicherzustellen, dass die Projektmappe auf dem Entwicklungscomputer und auf Endbenutzercomputern ausgeführt werden kann:  
  
-   Entfernen Sie das <xref:System.Security.SecurityTransparentAttribute> aus dem Projekt, wenn Sie ein Upgrade aus Visual Studio 2008 ausgeführt haben.  
  
-   Führen Sie einen Befehl **Clean** in Visual Studio aus, damit Sie das Projekt auf dem Entwicklungscomputer ausführen oder debuggen können.  
  
-   Aktualisieren Sie die .NET Framework\-Voraussetzung für das Projekt.  
  
-   Endbenutzer müssen außerdem die Projektmappe neu installieren, wenn Sie diese zuvor mit ClickOnce bereitgestellt haben, bevor Sie das Zielframework geändert haben.  
  
 Weitere Informationen zu den einzelnen Aufgaben finden Sie in den entsprechenden Abschnitten weiter unten.  
  
## Entfernen des Attributs "SecurityTransparent" aus Projekten, für die Sie ein Upgrade aus Visual Studio 2008 ausgeführt haben  
 Wenn Sie ein Upgrade für ein Office\-Projekt aus Visual Studio 2008 ausgeführt haben und sich das Zielframework des Projekts anschließend in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ändert, müssen Sie das <xref:System.Security.SecurityTransparentAttribute> aus dem Projekt entfernen. Visual Studio entfernt dieses Attribut nicht automatisch für Sie. Wenn Sie dieses Attribut nicht entfernen, erhalten Sie eine Fehlermeldung, wenn Sie das Projekt kompilieren.  
  
 Weitere Informationen zu den Bedingungen, unter denen Visual Studio das Zielframework eines aktualisierten Projekts in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ändern kann, finden Sie unter[Aktualisieren und Migrieren von Office-Projektmappen](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### So entfernen Sie "SecurityTransparentAttribute"  
  
1.  Öffnen Sie den **Projektmappen\-Explorer**, während das Projekt in Visual Studio geöffnet ist.  
  
2.  Doppelklicken Sie unter dem Knoten **Eigenschaften** \(für C\#\) oder dem Knoten **Mein Projekt** \(für Visual Basic\) auf die Codedatei "AssemblyInfo", um diese im Code\-Editor zu öffnen.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten müssen Sie im **Projektmappen\-Explorer** auf die Schaltfläche **Alle Dateien anzeigen** klicken, um die Codedatei "AssemblyInfo" anzuzeigen.  
  
3.  Suchen Sie nach <xref:System.Security.SecurityTransparentAttribute>, und entfernt Sie das Attribut aus der Datei, oder kommentieren Sie es aus.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## Ausführen des Befehls "Bereinigen" zum Debuggen oder Ausführen eines Projekts auf dem Entwicklungscomputer  
 Wenn ein Office\-Projekt erstellt wurde, bevor das Zielframework des Projekts in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie einen Befehl **Bereinigen** ausführen und dann das Projekt neu erstellen, nachdem das Zielframework geändert wurde.  Wenn Sie keinen Befehl **Bereinigen** ausführen, erhalten Sie eine <xref:System.Runtime.InteropServices.COMException> beim Versuch, das Projekt mit dem neuen Zielframework zu debuggen oder auszuführen.  
  
 Weitere Informationen zum Befehl **Bereinigen** finden Sie unter [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
## Aktualisieren der Voraussetzungen für die Bereitstellung  
 Wenn Sie als neues Zielframework für ein Office\-Projekt [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher verwenden, müssen Sie auch die entsprechende .NET Framework\-Voraussetzung im Dialogfeld **Voraussetzungen** aktualisieren.  Andernfalls sucht die ClickOnce\-Bereitstellung oder das InstallShield Limited Edition\-Projekt nach einer früheren Version von .NET Framework und installiert diese.  
  
 Weitere Informationen zum Aktualisieren der Voraussetzungen für die Bereitstellung auf Endbenutzercomputern finden Sie unter [Vorgehensweise: Installieren von erforderlichen Komponenten auf Endbenutzercomputern für die Ausführung von Office\-Projektmappen](http://msdn.microsoft.com/de-de/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## Erneutes Installation von Projektmappen auf Endbenutzercomputern  
 Wenn Sie mithilfe von ClickOnce eine Office\-Projektmappe bereitstellen, die als Zielframework .NET Framework 3.5 verwendet, und dann das Projekt auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher umstellen, müssen Endbenutzer die Projektmappe deinstallieren und dann erneut installieren, nachdem Sie sie veröffentlicht haben.  Wenn Sie die Projektmappe mit dem neuen Zielframework erneut veröffentlichen und die Lösung auf Endbenutzercomputern aktualisiert wird, erhalten Benutzer eine <xref:System.Runtime.InteropServices.COMException>, wenn sie die aktualisierte Lösung ausführen.  
  
## Siehe auch  
 [Migrieren von Office-Projektmappen in .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  