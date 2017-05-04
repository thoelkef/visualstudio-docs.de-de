---
title: "Gewusst wie: Hinzuf&#252;gen und Entfernen zus&#228;tzlicher Assemblys | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.RAD.CustomAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Pakete"
ms.assetid: d9d1e8db-9df2-4e07-ac8d-59ef05d24090
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Gewusst wie: Hinzuf&#252;gen und Entfernen zus&#228;tzlicher Assemblys
  Wenn ein SharePoint\-Paket im Hinblick auf Funktionen oder Daten von anderen Assemblys abhängig ist, können Sie die Assemblys dem Lösungspaket \(.wsp\) hinzufügen.  Auf diese Weise stellt der SharePoint\-Server sicher, dass benutzerdefinierte Assemblys mit einem Paket installiert werden.  
  
 Sie können auch die zugeordneten sicheren Steuerelemente und Klassenressourcendateien der Assemblys hinzufügen und ändern.  
  
## Hinzufügen von zusätzlichen Assemblys, sicheren Steuerelementen und Klassenressourcen  
 Sie können im SharePoint\-Lösungspaket zusätzliche Assemblys hinzufügen.  Zusätzliche Assemblys in einer Sandkastenlösung werden im globalen Assemblycache bereitgestellt, die SharePoint\-Projektelemente in einer Sandkastenlösung werden jedoch der Inhaltsdatenbank hinzugefügt.  Darüber hinaus können Sie diesen zusätzlichen Assemblys sichere Steuerelemente und Klassenressourcen hinzufügen.  Weitere Informationen zu sicheren Steuerelementen finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) oder "Erstellen eines SafeControl\-Eintrags" in [Bereitstellen von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### So fügen Sie eine vorhandene Assembly hinzu  
  
1.  Öffnen Sie den **Paket\-Designer**.  Weitere Informationen finden Sie unter [Gewusst wie: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wählen Sie die Registerkarte **Erweitert** aus.  
  
3.  Wählen Sie die Schaltfläche **Hinzufügen** aus, und wählen Sie dann aus der Liste **Vorhandene Assembly hinzufügen** aus.  
  
     Das Dialogfeld **Vorhandene Assembly hinzufügen** wird angezeigt.  
  
4.  Wählen Sie das Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.png "Auslassungszeichen im ASP.NET Mobile-Designer")\) aus, und wählen Sie dann die Assembly aus, die Sie hinzufügen möchten.  Aus Gründen der Portabilität wird empfohlen, einen relativen Pfad zur ausgewählten Assembly zu verwenden.  
  
5.  Wählen Sie für das **Bereitstellungsziel** die Optionsschaltfläche **GlobalAssemblyCache** aus, um die Assembly im globalen Assemblycache bereitzustellen, oder wählen Sie die Optionsschaltfläche **WebApplication** aus, um die Assembly im Ordner "WebApplication" auf dem Server, der SharePoint ausführt, bereitzustellen.  
  
#### So fügen Sie eine Assembly aus der Projektausgabe hinzu  
  
1.  Öffnen Sie den **Paket\-Designer**.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wählen Sie die Registerkarte **Erweitert** aus.  
  
3.  Wählen Sie die Schaltfläche **Hinzufügen** aus, und wählen Sie dann **Assembly aus Projektausgabe hinzufügen** aus der Liste aus.  
  
     Das Dialogfeld **Assembly aus Projektausgabe hinzufügen** wird angezeigt.  
  
4.  In der Liste **Quellprojekt**, und wählen Sie das Quellprojekt aus, das Sie hinzufügen möchten.  
  
5.  Wählen Sie für das **Bereitstellungsziel** die Optionsschaltfläche **GlobalAssemblyCache** aus, um die Assembly im globalen Assemblycache bereitzustellen, oder wählen Sie die Optionsschaltfläche **WebApplication** aus, um die Assembly im Ordner "WebApplication" auf dem Server, der SharePoint ausführt, bereitzustellen.  
  
#### So fügen Sie ein sicheres Steuerelement hinzu  
  
1.  Öffnen Sie das Dialogfeld **Vorhandene Assembly bearbeiten**.  Öffnen Sie hierzu den Paket\-Designer, wählen Sie die Registerkarte **Erweitert** aus, wählen Sie eine Assembly aus, und klicken Sie dann auf die Schaltfläche **Bearbeiten**.  
  
2.  Wählen Sie im Bereich **Sichere Steuerelemente** die Schaltfläche **Klicken Sie hier, um ein neues Element hinzuzufügen** aus.  
  
3.  Geben Sie in der Spalte **Assemblyname** den Namen der Assembly ein.  
  
4.  Geben Sie in der Spalte **Namespace** den Namen des Namespace für das sichere Steuerelement ein.  
  
5.  Geben Sie in der Spalte **Typname** den Namen des Typs ein.  
  
#### So fügen Sie eine Klassenressource hinzu  
  
1.  Öffnen Sie das Dialogfeld **Vorhandene Assembly bearbeiten**.  Öffnen Sie hierzu den Paket\-Designer, wählen Sie die Registerkarte **Erweitert** aus, wählen Sie eine Assembly aus, und klicken Sie dann auf die Schaltfläche **Bearbeiten**.  
  
2.  Wählen Sie im Bereich **Klassenressourcen** die Schaltfläche **Klicken Sie hier, um ein neues Element hinzuzufügen** aus.  
  
3.  Wählen Sie in der Spalte **Dateiname** das Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.png "Auslassungszeichen im ASP.NET Mobile-Designer")\) aus, und wählen Sie die Klassenressource aus, die Sie hinzufügen möchten.  
  
## Löschen von benutzerdefinierten Assemblys  
 Sie können Assemblys aus einem SharePoint\-Paket oder sichere Steuerelemente und Klassenressourcen aus vorhandenen Assemblys löschen.  
  
#### So löschen Sie eine vorhandene Assembly  
  
1.  Öffnen Sie den **Paket\-Designer**.  Weitere Informationen finden Sie unter [Gewusst wie: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wählen Sie die Registerkarte **Erweitert** aus.  
  
3.  Wählen Sie im Bereich **Zusätzliche Assemblys** die benutzerdefinierte Assembly aus, die Sie löschen möchten.  
  
4.  Wählen Sie die Schaltfläche **Löschen** aus.  
  
#### So löschen Sie ein sicheres Steuerelement für eine Assembly  
  
1.  Öffnen Sie das Dialogfeld **Vorhandene Assembly bearbeiten**.  Öffnen Sie hierzu den Paket\-Designer, wählen Sie die Registerkarte **Erweitert** aus, wählen Sie eine Assembly aus, und klicken Sie dann auf die Schaltfläche **Bearbeiten**.  
  
2.  Wählen Sie das zu löschende sichere Steuerelement aus.  
  
3.  Wählen Sie die ENTF\-TASTE aus.  
  
#### So löschen Sie eine Klassenressource für eine Assembly  
  
1.  Öffnen Sie das Dialogfeld **Vorhandene Assembly bearbeiten**.  Öffnen Sie hierzu den Paket\-Designer, wählen Sie die Registerkarte **Erweitert** aus, wählen Sie eine Assembly aus, und klicken Sie dann auf die Schaltfläche **Bearbeiten**.  
  
2.  Wählen Sie die zu löschende Klassenressource aus.  
  
3.  Wählen Sie die ENTF\-TASTE aus.  
  
## Siehe auch  
 [Erstellen von SharePoint-Funktionen](../sharepoint/creating-sharepoint-features.md)   
 [Gewusst wie: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Gewusst wie: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [NIB: Building SharePoint Solutions with Team Foundation Server](http://msdn.microsoft.com/de-de/700a570a-e98e-4425-aadd-34c014868d43)  
  
  