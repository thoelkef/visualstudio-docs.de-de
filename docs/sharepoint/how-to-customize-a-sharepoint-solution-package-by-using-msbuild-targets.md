---
title: 'Vorgehensweise: Anpassen eines SharePoint-Lösungspakets mithilfe von MSBuild-Ziele | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 90358624f5de8fc7c90e3424f04617acab4388a4
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2018
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Gewusst wie: Anpassen eines SharePoint-Lösungspakets mithilfe von MSBuild-Zielen
  Mithilfe von MSBuild-Ziele an der Eingabeaufforderung können Sie anpassen, wie Visual Studio SharePoint-Paketdateien (.wsp) erstellt. Beispielsweise können Sie anpassen, die MSBuild-Eigenschaften zum Ändern der Verpackung Zwischenverzeichnis befinden und die MSBuild-Element-Gruppen, die aufgelisteten Dateien angeben.  
  
## <a name="customizing-and-running-msbuild-targets"></a>Anpassen und Ausführen von MSBuild-Ziele  
 Wenn Sie die Ziele BeforeLayout und AfterLayout anpassen, können Sie Aufgaben vor dem Paketlayouts, z. B. hinzufügen, entfernen oder Ändern von Dateien, die gepackt werden ausführen.  
  
#### <a name="to-customize-the-beforelayout-target"></a>Das Ziel BeforeLayout anpassen  
  
1.  Öffnen eines Editors, z. B. Notepad, und fügen Sie den folgenden Code hinzu.  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     Dieses Beispiel zeigt eine Meldung vor der Verpackung des Ziels.  
  
2.  Nennen Sie die Datei **CustomLayout.SharePoint.targets**, und speichern Sie sie in den Ordner für die SharePoint-Projekt.  
  
3.  Öffnen Sie das Projekt, öffnen Sie das Kontextmenü und wählen Sie dann **Projekt entladen**.  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **bearbeiten***Projektname***vbproj** oder **bearbeiten***Projektname*** csproj**.  
  
5.  Nach der `Import` Zeile am Ende der Projektdatei, fügen Sie die folgende Zeile hinzu.  
  
    ```xml  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Speichern und schließen Sie die Projektdatei.  
  
7.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Projekt erneut laden**.  
  
 Wenn Sie das Projekt veröffentlichen, wird die Nachricht in der Ausgabe angezeigt, vor Beginn der Verpackung.  
  
#### <a name="to-customize-the-afterlayout-target"></a>Das Ziel AfterLayout anpassen  
  
1.  Wählen Sie in der Menüleiste **Datei**, **öffnen**, **Datei**.  
  
2.  In der **Dateiöffnungsmodus** (Dialogfeld), navigieren Sie zum Projektordner, wählen Sie die Datei CustomLayout.target, und wählen Sie dann die **öffnen** Schaltfläche.  
  
3.  Kurz vor dem Ausführen der `</Project>` zu kennzeichnen, fügen Sie den folgenden Code hinzu:  
  
    ```xml  
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
  
  