---
title: "Exemplarische Vorgehensweise: Aufrufe in das Visual Studio SDK mithilfe der Automatisierung | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exemplarische Vorgehensweisen [Visual Studio SDK], Aufrufe mit Automatisierung"
ms.assetid: ca4dab48-632c-4c2a-8c84-57c027e37987
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Exemplarische Vorgehensweise: Aufrufe in das Visual Studio SDK mithilfe der Automatisierung
In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie ein Visual Studio\-Add\-In erstellen, das einen Visual Studio\-Dienst nutzt. Das erstellte Add\-In ruft einen Dienstanbieter ab und verwendet diesen zum Abrufen eines Diensts. Auf die gleiche Weise können Sie alle angebotenen Visual Studio\-Dienste abrufen. Weitere Informationen zu Diensten und Dienstanbietern finden Sie unter [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md). Anhand der folgenden Vorgehensweisen wird veranschaulicht, wie Sie ein Add\-In erstellen und dann einen Dienst über das Add\-In abrufen.  
  
## Erstellen eines Add\-Ins  
 In diesem Abschnitt erstellen Sie ein Visual Studio\-Add\-In mithilfe der Add\-In\-Projektvorlage von Visual Studio.  
  
#### So erstellen Sie ein Add\-In  
  
1.  Erstellen Sie ein neues Visual Studio\-Projekt \(**Datei \> Neu \> Projekt**\).  
  
2.  Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** den Knoten **Andere Projekttypen**, und klicken Sie dann auf den Knoten **Erweiterungen**. Wählen Sie **Visual Studio\-Add\-In** aus.  
  
3.  Erstellen Sie ein neues Add\-In\-Projekt mit dem Namen `Addin`.  
  
     Klicken Sie im Add\-In\-Assistenten von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Wählen Sie eine Programmiersprache aus** die Option **Ein Add\-In mit Visual C\# erstellen** oder **Ein Add\-In mit Visual Basic erstellen** aus.  
  
5.  Wählen Sie auf der Seite **Wählen Sie einen Anwendungshost aus** die Option **Microsoft Visual Studio \<Version\>** aus.  
  
6.  Geben Sie auf der Seite **Geben Sie einen Namen und eine Beschreibung ein** im Feld **Name** die Zeichenfolge `MyAddin` und im Feld **Beschreibung** die Zeichenfolge `MyAddin Walkthrough` ein.  
  
7.  Wählen Sie auf der Seite **Wählen Sie die Add\-In\-Optionen aus** unter **Soll eine Befehlszeilen\-Benutzeroberfläche für das Add\-In erstellt werden?** die Option zum Erstellen eines Menüelements unter "Extras" aus. Deaktivieren Sie die anderen Kontrollkästchen.  
  
8.  Übernehmen Sie alle anderen Standardeinstellungen.  
  
9. Erstellen Sie die Projektmappe, und stellen Sie sicher, dass sie fehlerfrei kompiliert wird.  
  
## Abrufen eines Diensts über ein Add\-In  
 In den folgenden Schritten werden Sie durch den Vorgang zum Abrufen eines Diensts über Ihr Add\-In geführt.  
  
#### So rufen Sie einen Dienst ab  
  
1.  Öffnen Sie die Datei "Connect.cs" oder "Connect.vb", und fügen Sie der `using`\- \(C\#\) bzw. `Imports`\-Anweisung \(Visual Basic\) die folgenden Zeilen hinzu:  
  
     [!code-cs[VSSDKAddin#1](../misc/codesnippet/CSharp/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_1.cs)]
     [!code-vb[VSSDKAddin#1](../misc/codesnippet/VisualBasic/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_1.vb)]  
  
2.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Projektknoten, und fügen Sie die folgenden .NET\-Verweise hinzu:  
  
    ```  
    Microsoft.VisualStudio.OLE.Interop Microsoft.VisualStudio.Shell.Interop  
    ```  
  
3.  Fügen Sie der `if(commandName == "Addin.Connect.Addin")`\- oder `If commandName = "Addin.Connect.Addin" Then`\-Klausel der `Exec`\-Methode die folgenden Codezeilen hinzu:  
  
     [!code-cs[VSSDKAddin#2](../misc/codesnippet/CSharp/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_2.cs)]
     [!code-vb[VSSDKAddin#2](../misc/codesnippet/VisualBasic/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_2.vb)]  
  
     Dieser Code wandelt das aktuelle Anwendungsobjekt \(Typ `DTE2`\) in ein `IOleServiceProvider`\-Objekt um und ruft dann `QueryService` auf, um den <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>\-Dienst abzurufen. Dieser Dienst stellt eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>\-Schnittstelle bereit. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A>\-Methode zeigt ein Meldungsfeld an, wenn das Add\-In ausgeführt wird.  
  
4.  Erstellen und starten Sie das Add\-In\-Projekt im Debugmodus, indem Sie F5 drücken.  
  
     Dadurch wird eine weitere Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gestartet.  
  
5.  Klicken Sie in der neuen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Instanz im Menü **Extras** auf **Add\-In**. Im Meldungsfeld wird Folgendes angezeigt:  
  
    ```  
    MyAddin Inside Addin.Connect  
    ```  
  
## Siehe auch  
 [Gewusst wie: Deaktivieren und Entfernen von Add\-Ins](../Topic/How%20to:%20Deactivate%20and%20Remove%20an%20Add-In.md)