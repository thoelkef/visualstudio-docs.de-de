---
title: 'Vorgehensweise: Hinzufügen und Entfernen zusätzlicher Assemblys | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 242ba7fa389a832b1299f00c47ba22a67efc5fbc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873638"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Vorgehensweise: Fügen Sie hinzu und entfernen Sie zusätzlicher Assemblys
  Wenn ein SharePoint-Paket im Hinblick auf Funktionen oder Daten von anderen Assemblys abhängig ist, können Sie die Assemblys dem Lösungspaket (.wsp) hinzufügen. Auf diese Weise stellt der SharePoint-Server sicher, dass benutzerdefinierte Assemblys mit einem Paket installiert werden.  
  
 Sie können auch die zugeordneten sicheren Steuerelemente und Klassenressourcendateien der Assemblys hinzufügen und ändern.  
  
## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Hinzufügen von zusätzlichen Assemblys sichere Steuerelemente und Klassenressourcen  
 Sie können im SharePoint-Lösungspaket zusätzliche Assemblys hinzufügen. Zusätzliche Assemblys in einer Sandkastenlösung werden im globalen Assemblycache bereitgestellt, die SharePoint-Projektelemente in einer Sandkastenlösung werden jedoch der Inhaltsdatenbank hinzugefügt. Darüber hinaus können Sie diesen zusätzlichen Assemblys sichere Steuerelemente und Klassenressourcen hinzufügen. Weitere Informationen zu sicheren Steuerelementen finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) oder "Erstellen eines SafeControl-Eintrags" in [Bereitstellen von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### <a name="to-add-an-existing-assembly"></a>So fügen Sie eine vorhandene Assembly hinzu  
  
1.  Öffnen der **Paket-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wählen Sie die **erweitert** Registerkarte.  
  
3.  Wählen Sie die **hinzufügen** Schaltfläche, und wählen Sie dann **vorhandene Assembly hinzufügen** aus der Liste.  
  
     Die **vorhandene Assembly hinzufügen** Dialogfeld wird angezeigt.  
  
4.  Wählen Sie die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")), und wählen Sie dann auf die Assembly, die Sie hinzufügen möchten. Aus Gründen der Portabilität wird empfohlen, einen relativen Pfad zur ausgewählten Assembly zu verwenden.  
  
5.  Für die **Bereitstellungsziel**, wählen Sie die **GlobalAssemblyCache** Optionsfeld aus, um die Assembly im globalen Assemblycache bereitstellen, oder wählen Sie die **WebApplication** Option Schaltfläche, um die Assembly im Ordner "WebApplication" auf dem Server bereitstellen, auf dem SharePoint ausgeführt wird.  
  
#### <a name="to-add-an-assembly-from-project-output"></a>So fügen Sie eine Assembly aus der Projektausgabe hinzu  
  
1.  Öffnen der **Paket-Designer**.  
  
     Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wählen Sie die **erweitert** Registerkarte.  
  
3.  Wählen Sie die **hinzufügen** Schaltfläche, und wählen Sie dann **Assembly aus Projektausgabe hinzufügen** aus der Liste.  
  
     Die **Assembly aus Projektausgabe hinzufügen** Dialogfeld wird angezeigt.  
  
4.  In der **Quellprojekt** aus, und wählen Sie das Quellprojekt, die Sie hinzufügen möchten.  
  
5.  Für die **Bereitstellungsziel**, wählen Sie die **GlobalAssemblyCache** Optionsfeld aus, um die Assembly im globalen Assemblycache bereitstellen, oder wählen Sie die **WebApplication** Option Schaltfläche, um die Assembly im Ordner "WebApplication" auf dem Server bereitstellen, auf dem SharePoint ausgeführt wird.  
  
#### <a name="to-add-a-safe-control"></a>So fügen Sie ein sicheres Steuerelement hinzu  
  
1.  Öffnen der **vorhandene Assembly bearbeiten** Dialogfeld. Um dies zu erreichen, der Paket-Designer zu öffnen, wählen Sie die **erweitert** Registerkarte, wählen Sie eine Assembly und wählen Sie dann die **bearbeiten** Schaltfläche.  
  
2.  In der **sichere Steuerelemente** Bereich, wählen Sie die **klicken Sie hier, um ein neues Element hinzufügen** Schaltfläche.  
  
3.  In der **Assemblyname** Spalte Geben Sie den Namen der Assembly.  
  
4.  In der **Namespace** Spalte Geben Sie den Namen des Namespace für das sichere Steuerelement.  
  
5.  In der **Typnamen** Spalte Geben Sie den Namen des Typs.  
  
#### <a name="to-add-a-class-resource"></a>So fügen Sie eine Klassenressource hinzu  
  
1.  Öffnen der **vorhandene Assembly bearbeiten** Dialogfeld. Um dies zu erreichen, der Paket-Designer zu öffnen, wählen Sie die **erweitert** Registerkarte, wählen Sie eine Assembly und wählen Sie dann die **bearbeiten** Schaltfläche.  
  
2.  In der **Klassenressourcen** Bereich, wählen Sie die **klicken Sie hier, um ein neues Element hinzufügen** Schaltfläche.  
  
3.  In der **Dateiname** Spalte wählen Sie die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")), und wählen Sie die Klassenressource aus, die Sie hinzufügen möchten.  
  
## <a name="delete-custom-assemblies"></a>Löschen von benutzerdefinierten Assemblys  
 Sie können Assemblys aus einem SharePoint-Paket oder sichere Steuerelemente und Klassenressourcen aus vorhandenen Assemblys löschen.  
  
#### <a name="to-delete-an-existing-assembly"></a>So löschen Sie eine vorhandene Assembly  
  
1.  Öffnen der **Paket-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wählen Sie die **erweitert** Registerkarte.  
  
3.  In der **zusätzliche Assemblys** Bereich, wählen Sie die benutzerdefinierte Assembly, die Sie löschen möchten.  
  
4.  Wählen Sie die **löschen** Schaltfläche.  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>So löschen Sie ein sicheres Steuerelement für eine Assembly  
  
1.  Öffnen der **vorhandene Assembly bearbeiten** Dialogfeld. Um dies zu erreichen, der Paket-Designer zu öffnen, wählen Sie die **erweitert** Registerkarte, wählen Sie eine Assembly und wählen Sie dann die **bearbeiten** Schaltfläche.  
  
2.  Wählen Sie das zu löschende sichere Steuerelement aus.  
  
3.  Wählen Sie die ENTF-TASTE aus.  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>So löschen Sie eine Klassenressource für eine Assembly  
  
1.  Öffnen der **vorhandene Assembly bearbeiten** Dialogfeld. Um dies zu erreichen, der Paket-Designer zu öffnen, wählen Sie die **erweitert** Registerkarte, wählen Sie eine Assembly und wählen Sie dann die **bearbeiten** Schaltfläche.  
  
2.  Wählen Sie die zu löschende Klassenressource aus.  
  
3.  Wählen Sie die ENTF-TASTE aus.  
  
## <a name="see-also"></a>Siehe auch
 [Erstellen von SharePoint-features](../sharepoint/creating-sharepoint-features.md)   
 [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Vorgehensweise: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
