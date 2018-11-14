---
title: 'Vorgehensweise: Veröffentlichen eines Projekts, die einem bestimmten Gebietsschema | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca121a8f8a68ca7a036b14c0f0c2bd6d1a84ff00
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607587"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Gewusst wie: Veröffentlichen eines Projekts, die einem bestimmten Gebietsschema
Es ist nicht ungewöhnlich, dass eine Anwendung Komponenten mit unterschiedlichen Gebietsschemas enthält. In diesem Szenario würden Sie eine Projektmappe aus mehreren Projekten erstellen und dann gesonderte Projekte für jedes Gebietsschema veröffentlichen. Dieses Verfahren zeigt, wie Sie das erste Projekt in einer Projektmappe mit dem Gebietsschema "en" mit einem Makro veröffentlichen können. Wenn Sie das Verfahren mit einem anderen Gebietsschema als "en" verwenden möchten, müssen Sie `localeString` im Makro auf das verwendete Gebietsschema festlegen (beispielsweise auf "de" oder "de-DE").  
  
> [!NOTE]
>  Wenn Sie dieses Makro verwenden, sollte der Ort der Veröffentlichung eine gültige URL oder UNC-Freigabe (Universal Naming Convention) sein. Darüberhinaus müssen Internetinformationsdienste (Internet Information Services, IIS) auf Ihrem Computer installiert sein. So installieren Sie IIS, auf die **starten** Menü klicken Sie auf **Systemsteuerung**. Doppelklicken Sie auf **hinzufügen oder Entfernen von Programmen**. In **Software**, klicken Sie auf **Windows-Komponenten hinzufügen/entfernen**. In der **Assistenten für Windows-Komponenten**, wählen die **(Internet Information Services, IIS)** Kontrollkästchen in der **Komponenten** Liste. Klicken Sie dann auf **Fertig stellen** um den Assistenten zu schließen.  
  
### <a name="to-create-the-publishing-macro"></a>So erstellen Sie das Makro zum Veröffentlichen  
  
1.  So öffnen Sie im Makro-Explorer auf die **Tools** , zeigen Sie auf **Makros**, und klicken Sie dann auf **Makro-Explorer**.  
  
2.  Erstellen Sie ein neues Makromodul. Wählen Sie im Makro-Explorer **MyMacros**. Auf der **Tools** Startmenü **Makros**, und klicken Sie dann auf **neues Makromodul**. Nennen Sie das Modul **"PublishSpecificCulture"**.  
  
3.  Erweitern Sie im Makro-Explorer die **MyMacros** Knoten, und öffnen Sie die **PublishAllProjects** Modul, indem Sie darauf doppelklicken (oder von der **Tools** Menü **Makros**, und klicken Sie dann auf **Makro-IDE**).  
  
4.  Fügen Sie in der Makro-IDE dem Modul nach den `Import`-Anweisungen den folgenden Code hinzu:  
  
    ```vb  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certificate and the   
            ' security zone must be set.  
            Dim localeString As String = "en"  
  
            ' Get first project.  
            Dim proj As Project = DTE.Solution.Projects.Item(1)  
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value  
  
            ' GenerateManifests and SignManifests must always be set to  
            ' True for publishing to work.   
            proj.Properties.Item("GenerateManifests").Value = True  
            proj.Properties.Item("SignManifests").Value = True  
  
            'Set the publish language.  
            'This will set the deployment language and pick up all   
            ' en resource dlls:  
            Dim originalTargetCulture As String = _  
                publishProperties.Item("TargetCulture").Value  
            publishProperties.Item("TargetCulture").Value = localeString  
  
            'Append 'en' to end of publish, install, and update URLs if needed:  
            Dim originalPublishUrl As String = _  
                publishProperties.Item("PublishUrl").Value  
            Dim originalInstallUrl As String = _  
                publishProperties.Item("InstallUrl").Value  
            Dim originalUpdateUrl As String = _  
                publishProperties.Item("UpdateUrl").Value  
            publishProperties.Item("PublishUrl").Value = _  
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))  
            If originalInstallUrl <> String.Empty Then  
                publishProperties.Item("InstallUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))  
            End If  
            If originalUpdateUrl <> String.Empty Then  
                publishProperties.Item("UpdateUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))  
            End If  
            proj.Save()  
  
            Dim slnbld2 As SolutionBuild2 = _  
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)  
            slnbld2.Clean(True)  
  
            slnbld2.BuildProject( _  
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
            proj.UniqueName, True)  
  
            ' Only publish if build is successful.  
            If slnbld2.LastBuildInfo <> 0 Then  
                MsgBox("Build failed for " & proj.UniqueName)  
            Else  
                slnbld2.PublishProject( _  
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
                proj.UniqueName, True)  
                If slnbld2.LastPublishInfo = 0 Then  
                    MsgBox("Publish succeeded for " & proj.UniqueName _  
                    & vbCrLf & "." _  
                    & " Publish Language was '" & localeString & "'.")  
                Else  
                    MsgBox("Publish failed for " & proj.UniqueName)  
                End If  
            End If  
  
            ' Return URLs and target culture to their previous state.  
            publishProperties.Item("PublishUrl").Value = originalPublishUrl  
            publishProperties.Item("InstallUrl").Value = originalInstallUrl  
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl  
            publishProperties.Item("TargetCulture").Value = originalTargetCulture  
            proj.Save()  
        End Sub  
  
        Private Function AppendStringToUrl(ByVal str As String, _  
        ByVal baseUri As Uri) As String  
            Dim returnValue As String = baseUri.OriginalString  
            If baseUri.IsFile OrElse baseUri.IsUnc Then  
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)  
            Else  
                If Not baseUri.ToString.EndsWith("/") Then  
                    returnValue = baseUri.OriginalString & "/" & str  
                Else  
                    returnValue = baseUri.OriginalString & str  
                End If  
            End If  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
5.  Schließen Sie die Makro-IDE. Der Fokus wechselt wieder zu Visual Studio.  
  
### <a name="to-publish-a-project-for-a-specific-locale"></a>So veröffentlichen Sie ein Projekt für ein bestimmtes Gebietsschema  
  
1.  Erstellen Sie ein Visual Basic Windows-Anwendungsprojekt auf die **Datei** Menü **neu**, und klicken Sie dann auf **Projekt**.  
  
2.  In der **neues Projekt** wählen Sie im Dialogfeld **Windows-Anwendung** aus der **Visual Basic** Knoten. Nennen Sie das Projekt *"PublishLocales"*.  
  
3.  Klicken Sie auf "Form1". In der **Eigenschaften** Fenster unter **Entwurf**, ändern Sie die **Sprache** Eigenschaft aus **(Standard)** zu **Englisch**. Ändern der **Text** -Eigenschaft des Formulars auf **"MyForm"**.  
  
     Beachten Sie, dass die lokalisierten Ressourcen-DLLs erst erstellt werden, wenn sie benötigt werden. Sie werden beispielsweise erstellt, wenn Sie den Text des Formulars oder eines der Steuerelemente ändern, nachdem Sie das neue Gebietsschema angegeben haben.  
  
4.  Veröffentlichen von *"PublishLocales"* mithilfe von Visual Studio-IDE.  
  
     In **Projektmappen-Explorer**Option *"PublishLocales"*. Auf der **Projekt** , wählen Sie im Menü **Eigenschaften**. Im Projekt-Designer auf die **veröffentlichen** Seite, geben Sie als Veröffentlichungsort **http://localhost/PublishLocales**, und klicken Sie dann auf **jetzt veröffentlichen**.  
  
     Wenn die veröffentlichte Webseite angezeigt wird, schließen Sie sie. (Für diesen Schritt müssen Sie das Projekt nur veröffentlichen, Sie müssen es nicht installieren.)  
  
5.  Veröffentlichen von *"PublishLocales"* erneut, indem Sie das Makro in das Fenster von Visual Studio-Eingabeaufforderung aufrufen. Anzeigen im Eingabeaufforderungsfenster auf den **anzeigen** , zeigen Sie auf **andere Windows** , und klicken Sie dann auf **Befehlsfenster**, oder drücken Sie **STRG** + **Alt**+**ein**. Geben Sie im Eingabeaufforderungsfenster Befehl `macros`, automatische Vervollständigung wird eine Liste der verfügbaren Makros bieten. Wählen Sie das folgende Makro aus, und drücken Sie die EINGABETASTE:  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  Wenn der Veröffentlichungsprozess erfolgreich ist, generiert er eine Nachricht "veröffentlichen, die für den *Publishlocales\publishlocales*. und dass die Sprache für die Veröffentlichung "en" war. Klicken Sie auf **OK** in der MessageBox. Wenn die Veröffentlichungswebseite angezeigt wird, klicken Sie auf **installieren**.  
  
7.  Suchen Sie im *C:\Inetpub\wwwroot\PublishLocales\en*. Daraufhin sollte die installierten Dateien wie Manifeste, *setup.exe*, und die veröffentlichte Webseitendatei sowie die lokalisierte Ressourcen-DLL. (Standardmäßig fügt ClickOnce eine *".deploy"* Erweiterung an EXEs und DLLs; Sie können diese Erweiterung entfernen, nach der Bereitstellung.)  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Makros-Entwicklungsumgebung](/previous-versions/visualstudio/visual-studio-2010/fb30sxt3(v=vs.100))   
 [Makro-Explorer-Fenster](/previous-versions/visualstudio/visual-studio-2010/wwkx67sw(v=vs.100))   
 [Gewusst wie: Bearbeiten und Programmgesteuertes Erstellen von Makros](/previous-versions/visualstudio/visual-studio-2010/k91y6132(v=vs.100))