---
title: 'Vorgehensweise: Markieren von Steuerelementen als sichere Steuerelemente | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
ms.assetid: 813727d5-6750-407c-a23e-c38dd611e78c
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e9f12b8944d9174ca885e90b92c8e3a0d0b83215
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Gewusst wie: Markieren von Steuerelementen als sichere Steuerelemente
  Aus Sicherheitsgründen unterscheidet SharePoint zwischen Web-Steuerelemente, die gegen Script-Injection geschützt sind und Web-Steuerelemente, die nicht aus. Steuerelemente, geschützt oder *sichere Steuerelemente*, von nicht vertrauenswürdigen Benutzern zugegriffen werden kann. Sie können Steuerelemente als sicher in der Einträge für sicheres Steuerelement-Eigenschaft des SharePoint-Projektelements oder im kennzeichnen die **Paket-Designer** beim Hinzufügen einer Assemblys für das Paket. Weitere Informationen finden Sie unter  
  
 [Datei "Web.config" Einstellungen ändern](http://go.microsoft.com/fwlink/?LinkId=178965) und [Registrieren einer Web-Teilassembly als ein sicheres Steuerelement](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Diese Prozeduren werden zur Veranschaulichung. Markieren von Steuerelementen sichere nur, wenn Sie sicher sind, dass sie sicher ist.  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Markieren sichere Steuerelemente in der Eigenschaft der Einträge für sicheres Steuerelement  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>So markieren Sie Steuerelemente als sicher oder unsicher ist, in der Eigenschaft Einträge für sicheres Steuerelement  
  
1.  Erstellen Sie eine SharePoint-Lösung, mit der ein visuelles Webpart-Projekt.  
  
2.  Zwei Steuerelemente zum Webpart hinzufügen: ein Textfeld und einer Schaltfläche. Ändern Sie die Namen bzw. die Standardwerte, TextBox1 und Button1.  
  
3.  Fügen Sie zwei Einträge auf des Webparts **Einträge für sicheres Steuerelement** Eigenschaft. Zu diesem Zweck die Schaltfläche mit den Auslassungszeichen (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) neben der **Einträge für sicheres Steuerelement** Eigenschaft in der  **Eigenschaften** Fenster.  
  
     Die **Einträge für sicheres Steuerelement** Dialogfeld wird angezeigt.  
  
4.  In der **Einträge für sicheres Steuerelement** Dialogfeld Wählen Sie die **hinzufügen** Schaltfläche zweimal, um zwei Einträge für sichere Steuerelemente zum Hinzufügen der **Elemente** Bereich: eine für die Schaltfläche "" und eine für das Textfeld.  
  
5.  Wählen Sie den ersten Eintrag für sichere Steuerelemente, und ändern Sie den Wert des seine **sicher** Eigenschaft **"false"**, dessen **Typnamen** Eigenschaft **Button1**, und die zugehörige **sicher für Skript** Eigenschaft **"false"**.  
  
     Dieser Schritt identifiziert das Schaltflächen-Steuerelement als Steuerelement und unsafe.  
  
6.  Wählen Sie den zweiten Sicherheitskontrolle-Eintrag in der Liste aus. Lassen Sie den Wert des seine **sichere** Eigenschaft als **"true"** und legen Sie seine **Typnamen** Eigenschaft, um **TextBox1** und seine **sicher Für Skript** Eigenschaft **"true"**.  
  
     Das Textfeld-Steuerelement ist nun als Steuerelement markiert, die für Script-Injection sicher ist.  
  
7.  Wählen Sie die Schaltfläche **OK** aus, um das Dialogfeld zu schließen.  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>Markieren sichere Steuerelemente im Paket-Designer  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>So markieren Sie Steuerelemente als sicher oder unsicher im Paket-Designer  
  
1.  Erstellen Sie eine SharePoint-Lösung, mit der ein visuelles Webpart-Projekt.  
  
2.  Zwei Steuerelemente zum Webpart hinzufügen: ein Textfeld und einer Schaltfläche. Ändern Sie die Namen bzw. die Standardwerte, TextBox1 und Button1.  
  
     Notieren Sie sich den Namespace des Steuerelements, da er später verwendet wird.  
  
3.  Wählen Sie in der Menüleiste **erstellen**, **Projektmappe** zum Erstellen des Projekts.  
  
4.  Erstellen Sie eine andere SharePoint-Lösung.  
  
5.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die Datei "Package.Package", und wählen Sie dann **öffnen** So öffnen die **Paket-Designer**.  
  
6.  In der **Paket-Designer**, wählen Sie die **erweitert** Registerkarte.  
  
7.  Klicken Sie unter **zusätzliche Assemblys**, wählen Sie die **hinzufügen** aus, und klicken Sie dann **vorhandene Assembly hinzufügen** aus der Liste.  
  
8.  In der **vorhandene Assembly hinzufügen** Dialogfeld Wählen Sie die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) neben  **Quellpfad**.  
  
9. Wählen Sie die Assembly aus der SharePoint-Lösung, die Sie in Schritt 1 erstellt haben, und wählen Sie dann die **öffnen** Schaltfläche.  
  
10. In diesem Beispiel lassen den **Bereitstellungsziel** Option GlobalAssemblyCache.  
  
     Dieser Schritt bewirkt, dass die Assembly mit dem System Global Assembly Cache (GAC) bereitgestellt. Wenn Sie die Assembly auf Webanwendungsordner ("bin") bereitstellen möchten, wählen Sie stattdessen die entsprechende Option. Weitere Informationen finden Sie unter [Bereitstellen von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. In der **sichere Steuerelemente** wählen Sie die **klicken Sie hier, um ein neues Element hinzufügen** Schaltfläche.  
  
12. Geben Sie die Werte für die Eigenschaften aus der folgenden Tabelle.  
  
    |Eigenschaftenname|Wert|  
    |-------------------|-----------|  
    |Namespace|Der vollqualifizierte Namespace für das Steuerelement, z. B. **BdcModelProject1.VisualWebPart1**.|  
    |Typname|Schaltfläche1|  
    |Assemblyname|Eine Assembly mit starke Namen, z. B.: Microsoft.Office.SharePoint.ClientExtensions, Version =-14.0.0.0, Culture = Neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Safe|Deaktivieren der **sichere** Kontrollkästchen.|  
    |Safe für Skripts|Lassen Sie die **sicher für Skript** Kontrollkästchen deaktivieren.|  
  
    > [!NOTE]  
    >  Die **Assemblyname** Wert für Assemblys, die über die **erweitert** auf der Registerkarte die **Paket-Designer** kann kein Token zu sein, muss er eine Assembly mit starkem Namen. Weitere Informationen finden Sie unter [Erstellen und Verwenden von Assemblys mit starkem Namen](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Wählen Sie die Tab-Taste, um einen weiteren Eintrag für sichere Steuerelemente zu erstellen.  
  
14. Wählen Sie die **klicken Sie hier, um ein neues Element hinzufügen** erneut.  
  
15. Geben Sie die Werte für die Eigenschaften aus der folgenden Tabelle.  
  
    |Eigenschaftenname|Wert|  
    |-------------------|-----------|  
    |Namespace|Der vollqualifizierte Namespace für das Steuerelement, z. B. **BdcModelProject1.VisualWebPart1**.|  
    |Typname|TextBox1|  
    |Assemblyname|Eine Assembly mit starke Namen, z. B.: Microsoft.Office.SharePoint.ClientExtensions, Version =-14.0.0.0, Culture = Neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Safe|Wählen Sie die **sichere** Kontrollkästchen.|  
    |Safe für Skripts|Wählen Sie die **sicher für Skript** Kontrollkästchen.|  
  
16. Wählen Sie die Tab-Taste, und wählen Sie dann die **OK** Schaltfläche, um das Dialogfeld zu schließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  