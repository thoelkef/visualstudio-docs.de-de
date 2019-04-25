---
title: 'Vorgehensweise: Markieren von Steuerelementen als sichere Steuerelemente | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0d2dfe0da64abb9540724c05d13b84715a684af0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082034"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Vorgehensweise: Markieren von Steuerelementen als sichere Steuerelemente
  Aus Sicherheitsgründen unterscheidet SharePoint zwischen Web-Steuerelemente, die vor der Script-Injection zu schützen und Web-Steuerelemente, die nicht aus. Steuerelemente, geschützt oder *sichere Steuerelemente*, über nicht vertrauenswürdige Benutzer zugegriffen werden kann. Sie können Steuerelemente wie in der Einträge für sicheres Steuerelement-Eigenschaft des SharePoint-Projektelements oder im abgesicherten markieren die **-Paket-Designer** beim Hinzufügen einer Assemblys für das Paket. Weitere Informationen finden Sie unter

- [Datei "Web.config" Ändern der Einstellungen](http://go.microsoft.com/fwlink/?LinkId=178965) und [Registrieren einer Web Part-Assembly als sicheres Steuerelement](http://go.microsoft.com/fwlink/?LinkId=171013).

> [!IMPORTANT]
>  Diese Prozeduren sind zur Veranschaulichung. Markieren von Steuerelementen sicher sind, nur, wenn Sie sicher sind, dass sie geschützt sind.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Sichere Steuerelemente in der Eigenschaft für sicheres Steuerelement Einträge markieren

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>So markieren Sie Steuerelemente wie sicher oder unsicher in der Eigenschaft für sicheres Steuerelement Einträge

1. Erstellen Sie eine SharePoint-Lösung mit einem Visual Web Part-Projekt.

2. Zwei Steuerelemente zum Webpart hinzufügen: ein Textfeld und eine Schaltfläche. Lassen Sie die Namen bzw. auf die Standardwerte, TextBox1 "und" Button1 ".

3. Fügen Sie zwei Einträge, um des Webparts **Einträge für sicheres Steuerelement** Eigenschaft. Zu diesem Zweck wählen Sie die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) neben dem **Einträge für sicheres Steuerelement** -Eigenschaft in der  **Eigenschaften** Fenster.

     Die **Einträge für sicheres Steuerelement** Dialogfeld wird angezeigt.

4. In der **Einträge für sicheres Steuerelement** Dialogfeld wählen die **hinzufügen** Schaltfläche zweimal, um zwei Einträge für sicheres Steuerelement zum Hinzufügen der **Mitglieder** Bereich: eine für die Schaltfläche und eine für das Textfeld.

5. Wählen Sie den ersten Eintrag für sicheres Steuerelement aus, und ändern Sie den Wert des der **sicher** Eigenschaft **"false"**, dessen **Typnamen** Eigenschaft **"Button1"**, und die zugehörige **sicher für Skript** Eigenschaft **"false"**.

     Dieser Schritt identifiziert das Schaltflächen-Steuerelement als ein nicht sicheres Steuerelement.

6. Wählen Sie den zweiten Eintrag für sicheres Steuerelement in der Liste aus. Lassen Sie den Wert des der **sicher** Eigenschaft als **"true"** und legen Sie seine **Typnamen** Eigenschaft, um **TextBox1** und dessen **sicher Vor Skripteinschleusung** Eigenschaft **"true"**.

     Das Textfeld-Steuerelement ist nun als Steuerelement markiert, die sicher vor skripteinschleusung ist.

7. Wählen Sie die Schaltfläche **OK** aus, um das Dialogfeld zu schließen.

## <a name="marking-safe-controls-in-the-package-designer"></a>Markieren sichere Steuerelemente in der Paket-Designer

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>So markieren Sie Steuerelemente wie sicher oder unsicher im Paket-Designer

1. Erstellen Sie eine SharePoint-Lösung mit einem Visual Web Part-Projekt.

2. Zwei Steuerelemente zum Webpart hinzufügen: ein Textfeld und eine Schaltfläche. Lassen Sie die Namen bzw. auf die Standardwerte, TextBox1 "und" Button1 ".

     Notieren Sie sich den Namespace des Steuerelements aus, da sie später verwendet wird.

3. Wählen Sie auf der Menüleiste **erstellen** > **Projektmappe** zum Erstellen des Projekts.

4. Erstellen Sie eine andere SharePoint-Lösung.

5. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die *"Package.Package"* Datei, und wählen Sie dann **öffnen** zum Öffnen der **-Paket-Designer**.

6. In der **-Paket-Designer**, wählen Sie die **erweitert** Registerkarte.

7. Klicken Sie unter **zusätzliche Assemblys**, wählen Sie die **hinzufügen** Schaltfläche, und wählen Sie dann **vorhandene Assembly hinzufügen** aus der Liste.

8. In der **vorhandene Assembly hinzufügen** Dialogfeld auf die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) neben  **Quellpfad**.

9. Wählen Sie die Assembly aus der SharePoint-Lösung, die Sie in Schritt 1 erstellt haben, und wählen Sie dann die **öffnen** Schaltfläche.

10. In diesem Beispiel lassen den **Bereitstellungsziel** Option GlobalAssemblyCache.

     Dieser Schritt bewirkt, dass die Assembly dem globalen Assemblycache (GAC)-System bereitstellen. Wenn Sie die Assembly, auf den Ordner der Web-Anwendung (. Bin) bereitstellen möchten, wählen Sie stattdessen die Option. Weitere Informationen finden Sie unter [Bereitstellen von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).

11. In der **sichere Steuerelemente** wählen die **klicken Sie hier, um ein neues Element hinzufügen** Schaltfläche.

12. Geben Sie die Werte für die Eigenschaften aus der folgenden Tabelle.

    |Eigenschaftenname|Wert|
    |-------------------|-----------|
    |Namespace|Der vollqualifizierte Namespace für das Steuerelement, z. B. **BdcModelProject1.VisualWebPart1**.|
    |Typname|Schaltfläche1|
    |Assemblyname|Eine Assembly mit starke Namen, z. B.: Microsoft.Office.SharePoint.ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Safe|Deaktivieren der **sicher** Kontrollkästchen.|
    |Sicher vor Skripteinschleusung|Lassen Sie die **sicher für Skript** Kontrollkästchen deaktivieren.|

    > [!NOTE]
    >  Die **Assemblyname** Wert für Assemblys, die über eine hinzugefügt wurden die **erweitert** Registerkarte die **-Paket-Designer** kann kein Token zu sein, es muss eine Assembly mit starkem Namen. Weitere Informationen finden Sie unter [Erstellen und Verwenden von Assemblys mit starkem Namen](http://go.microsoft.com/fwlink/?LinkId=177513).

13. Wählen Sie die **Registerkarte** Taste, um einen anderen Eintrag für sicheres Steuerelement zu erstellen.

14. Wählen Sie die **klicken Sie hier, um ein neues Element hinzufügen** erneut.

15. Geben Sie die Werte für die Eigenschaften aus der folgenden Tabelle.

    |Eigenschaftenname|Wert|
    |-------------------|-----------|
    |Namespace|Der vollqualifizierte Namespace für das Steuerelement, z. B. **BdcModelProject1.VisualWebPart1**.|
    |Typname|TextBox1|
    |Assemblyname|Eine Assembly mit starke Namen, z. B.: Microsoft.Office.SharePoint.ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Safe|Wählen Sie die **sicher** Kontrollkästchen.|
    |Sicher vor Skripteinschleusung|Wählen Sie die **sicher für Skript** Kontrollkästchen.|

16. Wählen Sie die **Registerkarte** Taste, und wählen Sie dann die **OK** , um das Dialogfeld zu schließen.

## <a name="see-also"></a>Siehe auch
- [Angaben Sie zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Paket und Bereitstellung von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
