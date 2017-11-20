---
title: "Vorgehensweise: Hinzufügen und Entfernen zusätzlicher Assemblys | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: d9d1e8db-9df2-4e07-ac8d-59ef05d24090
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7b7859738ac1fe70bdca4cdca5d2dff1220a22b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Gewusst wie: Hinzufügen und Entfernen zusätzlicher Assemblys
  Wenn ein SharePoint-Paket im Hinblick auf Funktionen oder Daten von anderen Assemblys abhängig ist, können Sie die Assemblys dem Lösungspaket (.wsp) hinzufügen. Auf diese Weise stellt der SharePoint-Server sicher, dass benutzerdefinierte Assemblys mit einem Paket installiert werden.  
  
 Sie können auch die zugeordneten sicheren Steuerelemente und Klassenressourcendateien der Assemblys hinzufügen und ändern.  
  
## <a name="adding-additional-assemblies-safe-controls-and-class-resources"></a>Hinzufügen von zusätzlichen Assemblys, sicheren Steuerelementen und Klassenressourcen  
 Sie können im SharePoint-Lösungspaket zusätzliche Assemblys hinzufügen. Zusätzliche Assemblys in einer Sandkastenlösung werden im globalen Assemblycache bereitgestellt, die SharePoint-Projektelemente in einer Sandkastenlösung werden jedoch der Inhaltsdatenbank hinzugefügt. Darüber hinaus können Sie diesen zusätzlichen Assemblys sichere Steuerelemente und Klassenressourcen hinzufügen. Weitere Informationen zu sicheren Steuerelementen finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) oder "Erstellen einer SafeControl Entry" im [Bereitstellen von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### <a name="to-add-an-existing-assembly"></a>So fügen Sie eine vorhandene Assembly hinzu  
  
1.  Öffnen der **Paket-Designer**. Weitere Informationen finden Sie unter [wie: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wählen Sie die **erweitert** Registerkarte.  
  
3.  Wählen Sie die **hinzufügen** aus, und klicken Sie dann **vorhandene Assembly hinzufügen** aus der Liste.  
  
     Die **vorhandene Assembly hinzufügen** Dialogfeld wird angezeigt.  
  
4.  Wählen Sie die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")), und wählen Sie dann auf die Assembly, die Sie hinzufügen möchten. Aus Gründen der Portabilität wird empfohlen, einen relativen Pfad zur ausgewählten Assembly zu verwenden.  
  
5.  Für die **Bereitstellungsziel**, wählen Sie die **GlobalAssemblyCache** Optionsfeld, um die Assembly im globalen Assemblycache bereitzustellen, oder wählen die **WebApplication** Option Schaltfläche ", um die Assembly im Ordner" WebApplication "auf dem Server bereitzustellen, auf dem SharePoint ausgeführt wird.  
  
#### <a name="to-add-an-assembly-from-project-output"></a>So fügen Sie eine Assembly aus der Projektausgabe hinzu  
  
1.  Öffnen der **Paket-Designer**.  
  
     Weitere Informationen finden Sie unter [wie: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wählen Sie die **erweitert** Registerkarte.  
  
3.  Wählen Sie die **hinzufügen** aus, und klicken Sie dann **Assembly aus Projektausgabe hinzufügen** aus der Liste.  
  
     Die **Assembly aus Projektausgabe hinzufügen** Dialogfeld wird angezeigt.  
  
4.  In der **Quellprojekt** aus, und wählen Sie das Quellprojekt aus, die Sie hinzufügen möchten.  
  
5.  Für die **Bereitstellungsziel**, wählen Sie die **GlobalAssemblyCache** Optionsfeld, um die Assembly im globalen Assemblycache bereitzustellen, oder wählen die **WebApplication** Option Schaltfläche ", um die Assembly im Ordner" WebApplication "auf dem Server bereitzustellen, auf dem SharePoint ausgeführt wird.  
  
#### <a name="to-add-a-safe-control"></a>So fügen Sie ein sicheres Steuerelement hinzu  
  
1.  Öffnen der **vorhandene Assembly bearbeiten** (Dialogfeld). Um dies zu erreichen, öffnen Sie den Paket-Designer, wählen Sie die **erweitert** Registerkarte, wählen Sie eine Assembly, und wählen Sie dann die **bearbeiten**Schaltfläche.  
  
2.  In der **sichere Steuerelemente** Bereich, wählen Sie die **klicken Sie hier, um ein neues Element hinzufügen** Schaltfläche.  
  
3.  In der **Assemblyname** Spalte Geben Sie den Namen der Assembly.  
  
4.  In der **Namespace** Spalte Geben Sie den Namen des Namespaces für das sichere Steuerelement.  
  
5.  In der **Typnamen** Spalte Geben Sie den Namen des Typs.  
  
#### <a name="to-add-a-class-resource"></a>So fügen Sie eine Klassenressource hinzu  
  
1.  Öffnen der **vorhandene Assembly bearbeiten** (Dialogfeld). Um dies zu erreichen, öffnen Sie den Paket-Designer, wählen Sie die **erweitert** Registerkarte, wählen Sie eine Assembly, und wählen Sie dann die **bearbeiten** Schaltfläche.  
  
2.  In der **Klassenressourcen** Bereich, wählen Sie die **klicken Sie hier, um ein neues Element hinzufügen** Schaltfläche.  
  
3.  In der **Dateiname** Spalte Schaltfläche mit den Auslassungszeichen (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")), und wählen Sie die Klassenressource, die Sie hinzufügen möchten.  
  
## <a name="deleting-custom-assemblies"></a>Löschen von benutzerdefinierten Assemblys  
 Sie können Assemblys aus einem SharePoint-Paket oder sichere Steuerelemente und Klassenressourcen aus vorhandenen Assemblys löschen.  
  
#### <a name="to-delete-an-existing-assembly"></a>So löschen Sie eine vorhandene Assembly  
  
1.  Öffnen der **Paket-Designer**. Weitere Informationen finden Sie unter [wie: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wählen Sie die **erweitert** Registerkarte.  
  
3.  In der **zusätzliche Assemblys** Bereich, wählen Sie die benutzerdefinierte Assembly, die Sie löschen möchten.  
  
4.  Wählen Sie die **löschen** Schaltfläche.  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>So löschen Sie ein sicheres Steuerelement für eine Assembly  
  
1.  Öffnen der **vorhandene Assembly bearbeiten** (Dialogfeld). Um dies zu erreichen, öffnen Sie den Paket-Designer, wählen Sie die **erweitert** Registerkarte, wählen Sie eine Assembly, und wählen Sie dann die **bearbeiten** Schaltfläche.  
  
2.  Wählen Sie das zu löschende sichere Steuerelement aus.  
  
3.  Wählen Sie die ENTF-TASTE aus.  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>So löschen Sie eine Klassenressource für eine Assembly  
  
1.  Öffnen der **vorhandene Assembly bearbeiten** (Dialogfeld). Um dies zu erreichen, öffnen Sie den Paket-Designer, wählen Sie die **erweitert** Registerkarte, wählen Sie eine Assembly, und wählen Sie dann die **bearbeiten** Schaltfläche.  
  
2.  Wählen Sie die zu löschende Klassenressource aus.  
  
3.  Wählen Sie die ENTF-TASTE aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von SharePoint-Funktionen](../sharepoint/creating-sharepoint-features.md)   
 [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Vorgehensweise: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
  