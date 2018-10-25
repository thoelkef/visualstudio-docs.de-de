---
title: 'Vorgehensweise: Anpassen eines SharePoint-Lösungspakets mithilfe von MSBuild-Ziele | Microsoft-Dokumentation'
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
ms.openlocfilehash: 434d673c62d0b26efa1559db7d7d98747146fd2d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889683"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Gewusst wie: Anpassen eines SharePoint-Lösungspakets mithilfe von MSBuild-Ziele
  Durch die Verwendung von MSBuild-Ziele an einer Eingabeaufforderung können Sie anpassen, wie Visual Studio SharePoint-Paketdateien erstellt (*.wsp*). Beispielsweise können Sie anpassen, die MSBuild-Eigenschaften, um das Zwischenverzeichnis Verpacken und die MSBuild-Element-Gruppen, die angeben, die aufgelisteten Dateien zu ändern.  
  
## <a name="customize-and-run-msbuild-targets"></a>Anpassen und Ausführen von MSBuild-Ziele  
 Wenn Sie die Ziele BeforeLayout und AfterLayout anpassen, können Sie Aufgaben vor dem paketlayout, z. B. hinzufügen, entfernen oder Ändern von Dateien, die verpackt, ausführen.  
  
#### <a name="to-customize-the-beforelayout-target"></a>Das Ziel BeforeLayout anpassen  
  
1. Öffnen eines Editors, z. B. Editor, und fügen Sie den folgenden Code.  
  
   ```xml  
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
     <Target Name="BeforeLayout">  
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
     </Target>  
   </Project>  
   ```  
  
    Dieses Beispiel zeigt eine Meldung, bevor Sie dieses Ziel für die paketerstellung.  
  
2. Nennen Sie die Datei **CustomLayout.SharePoint.targets**, und klicken Sie dann in den Ordner für das SharePoint-Projekt zu speichern.  
  
3. Öffnen Sie das Projekt, öffnen Sie das Kontextmenü und wählen Sie dann **Projekt entladen**.  
  
4. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **bearbeiten**  *\<Projektname > vbproj* oder **Bearbeiten**  *\<Projektname > .csproj*.  
  
5. Nach der `Import` Zeile am Ende der Projektdatei, fügen Sie die folgende Zeile hinzu.  
  
   ```xml  
   <Import Project="CustomLayout.SharePoint.targets" />  
   ```  
  
6. Speichern und schließen Sie die Projektdatei.  
  
7. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Projekt erneut laden**.  
  
   Wenn Sie das Projekt veröffentlichen, wird die Nachricht vor dem Packen beginnt in der Ausgabe angezeigt.  
  
#### <a name="to-customize-the-afterlayout-target"></a>Das Ziel AfterLayout anpassen  
  
1. Wählen Sie auf der Menüleiste **Datei** > **öffnen** > **Datei**.  
  
2. In der **geöffnete Datei** navigieren Sie zum Projektordner, wählen Sie die Datei CustomLayout.target und wählen Sie dann im Dialogfeld die **öffnen** Schaltfläche.  
  
3. Kurz vor dem Ausführen der `</Project>` markieren, fügen Sie den folgenden Code hinzu:  
  
   ```xml  
   <Target Name="AfterLayout">  
     <Message Importance="high" Text="In the AfterLayout Target"></Message>  
   </Target>  
   ```  
  
    Dieses Beispiel zeigt eine Meldung an, nachdem dieses Ziel verpackt wird.  
  
4. Speichern Sie und schließen Sie die Zieldatei.  
  
5. Starten Sie Visual Studio neu, und öffnen Sie das Projekt.  
  
   Wenn Sie das Projekt veröffentlichen, die BeforeLayout Meldung vor dem Packen beginnt, und die AfterLayout-Meldung angezeigt wird, nach Abschluss der paketerstellung.  
  
## <a name="see-also"></a>Siehe auch
 [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
