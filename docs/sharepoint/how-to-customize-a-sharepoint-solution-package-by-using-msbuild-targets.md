---
title: "Vorgehensweise: Anpassen eines SharePoint-Lösungspakets mithilfe von MSBuild-Ziele | Microsoft Docs"
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
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 758cf3e62621c22f3f97dc62b70c745afb860b8a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Gewusst wie: Anpassen eines SharePoint-Lösungspakets mithilfe von MSBuild-Zielen
  Mithilfe von MSBuild-Ziele an der Eingabeaufforderung können Sie anpassen, wie Visual Studio SharePoint-Paketdateien (.wsp) erstellt. Beispielsweise können Sie anpassen, die MSBuild-Eigenschaften zum Ändern der Verpackung Zwischenverzeichnis befinden und die MSBuild-Element-Gruppen, die aufgelisteten Dateien angeben.  
  
## <a name="customizing-and-running-msbuild-targets"></a>Anpassen und Ausführen von MSBuild-Ziele  
 Wenn Sie die Ziele BeforeLayout und AfterLayout anpassen, können Sie Aufgaben vor dem Paketlayouts, z. B. hinzufügen, entfernen oder Ändern von Dateien, die gepackt werden ausführen.  
  
#### <a name="to-customize-the-beforelayout-target"></a>Das Ziel BeforeLayout anpassen  
  
1.  Öffnen eines Editors, z. B. Notepad, und fügen Sie den folgenden Code hinzu.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     Dieses Beispiel zeigt eine Meldung vor der Verpackung des Ziels.  
  
2.  Nennen Sie die Datei **CustomLayout.SharePoint.targets**, und speichern Sie sie in den Ordner für die SharePoint-Projekt.  
  
3.  Öffnen Sie das Projekt, öffnen Sie das Kontextmenü und wählen Sie dann **Projekt entladen**.  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **bearbeiten***Projektname***vbproj** oder **Bearbeiten***Projektname***csproj**.  
  
5.  Nach der `Import` Zeile am Ende der Projektdatei, fügen Sie die folgende Zeile hinzu.  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Speichern und schließen Sie die Projektdatei.  
  
7.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Projekt erneut laden**.  
  
 Wenn Sie das Projekt veröffentlichen, wird die Nachricht in der Ausgabe angezeigt, vor Beginn der Verpackung.  
  
#### <a name="to-customize-the-afterlayout-target"></a>Das Ziel AfterLayout anpassen  
  
1.  Wählen Sie in der Menüleiste **Datei**, **öffnen**, **Datei**.  
  
2.  In der **Dateiöffnungsmodus** (Dialogfeld), navigieren Sie zum Projektordner, wählen Sie die Datei CustomLayout.target, und wählen Sie dann die **öffnen** Schaltfläche.  
  
3.  Kurz vor dem Ausführen der `</Project>` zu kennzeichnen, fügen Sie den folgenden Code hinzu:  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     Dieses Beispiel zeigt eine Meldung an, nachdem dieses Ziel verpackt wird.  
  
4.  Speichern Sie und schließen Sie die Targets-Datei.  
  
5.  Starten Sie Visual Studio neu, und öffnen Sie das Projekt.  
  
 Wenn Sie das Projekt veröffentlichen, die BeforeLayout-Meldung angezeigt wird, bevor Verpackung gestartet wird, und die AfterLayout-Meldung wird angezeigt, nachdem paketerstellung abgeschlossen ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  