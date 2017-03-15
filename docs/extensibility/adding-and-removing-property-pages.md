---
title: "Hinzuf&#252;gen und Entfernen von Eigenschaftenseiten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Hinzufügen von Eigenschaftenseiten"
  - "Eigenschaftenseiten für Projekt Untertypen"
  - "Eigenschaftenseiten, entfernen"
ms.assetid: 34853412-ab8a-4caa-9601-7d0727b2985d
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Hinzuf&#252;gen und Entfernen von Eigenschaftenseiten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Projekt\-Designer stellt einen zentralen Ort zum Verwalten von Projekteigenschaften, \- einstellungen und von Ressourcen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]bereit.  Es wird als einzelnes Fenster in der integrierten Entwicklungsumgebung \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und enthält verschiedene Bereiche auf der rechten Seite, die durch die Registerkarten auf der linken Seite zugegriffen werden.  Die Bereiche \(oft als Eigenschaftenseiten\) im Projekt\-Designer hängt vom Projekttyp und Sprache.  Der Projekt\-Designer können mit dem **Eigenschaften** Befehl im Menü **Projekt** zugegriffen werden.  
  
 Ein Projekt untertyp muss häufig zusätzliche Eigenschaftenseiten im Projekt\-Designer anzeigen.  Ebenso müssen möglicherweise einige Projekt untertypen, dass die integrierte Eigenschaftenseiten entfernt werden.  Um ein auszuführen, muss das Projekt untertyp die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>\-Schnittstelle implementieren und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>\-Methode überschreiben.  Wenn Sie diese Methode überschreiben und `propId`\-Parameter, der einen der Werte der <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>\-Enumeration enthält, können Sie Projekteigenschaften filtern, hinzufügen oder entfernen.  Beispielsweise müssen Sie möglicherweise eine Seite anlagenabhängigen den Eigenschaftenseiten auf Hinzufügen.  Dazu müssen Sie anlagenabhängige Eigenschaftenseiten filtern und eine neue Seite der vorhandenen Liste dann auf Hinzufügen.  
  
## Hinzufügen und Entfernen von Eigenschaftenseiten im Projekt\-Designer  
  
#### So erstellen Sie eine Eigenschaftenseite im Projekt\-Designer entfernen  
  
1.  Überschreiben Sie die `GetProperty(uint itemId, int propId, out object property)`\-Methode, um Eigenschaftenseiten zu filtern und zu erhalten eine `clsids` Liste.  
  
    ```vb#  
    Protected Overrides int GetProperty(uint itemId, int propId, out object property)  
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer  
        'Use propId to filter configuration-independent property pages.  
        Select Case propId  
            ....   
            Case CInt(Fix(__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList))  
                'Get a semicolon-delimited list of clsids of the configuration-independent property pages  
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))  
                   Dim propertyPagesList As String = ((String)[property]).ToUpper(CultureInfo.InvariantCulture)  
                'Remove the property page here  
                   ....  
            ....  
        End Select  
            ....   
        Return MyBase.GetProperty(itemId, propId, [property])  
    End Function  
  
    ```  
  
    ```c#  
    protected override int GetProperty(uint itemId, int propId, out object property)  
    {  
        //Use propId to filter configuration-independent property pages.  
        switch (propId)  
        {  
            . . . .  
  
            case (int)__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList:  
                {  
                    //Get a semicolon-delimited list of clsids of the configuration-independent property pages  
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));  
                    string propertyPagesList = ((string)property).ToUpper(CultureInfo.InvariantCulture);  
                    //Remove the property page here  
                    . . . .  
                }  
             . . . .  
         }  
            . . . .  
        return base.GetProperty(itemId, propId, out property);  
    }  
    ```  
  
2.  Entfernen Sie die **Buildereignisse** Seite erhaltener `clsids` Liste.  
  
    ```vb#  
    Private buildEventsPageGuid As String = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}"  
    Private index As Integer = propertyPagesList.IndexOf(buildEventsPageGuid)  
    If index <> -1 Then  
        ' GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'  
        Dim index2 As Integer = index + buildEventsPageGuid.Length + 1  
        If index2 >= propertyPagesList.Length Then  
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(";"c)  
        Else  
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2)  
        End If  
    End If  
    'New property value  
    property = propertyPagesList  
    ```  
  
    ```c#  
    string buildEventsPageGuid = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}";  
    int index = propertyPagesList.IndexOf(buildEventsPageGuid);  
    if (index != -1)  
    {  
        // GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'  
        int index2 = index + buildEventsPageGuid.Length + 1;  
        if (index2 >= propertyPagesList.Length)  
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(';');  
        else  
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2);  
    }  
    //New property value  
    property = propertyPagesList;  
    ```  
  
#### So erstellen Sie eine Eigenschaftenseite im Projekt\-Designer hinzu  
  
1.  Erstellen Sie eine Eigenschaftenseite, die Sie hinzufügen möchten.  
  
    ```vb#  
    Class DeployPropertyPage  
            Inherits Form  
            Implements Microsoft.VisualStudio.OLE.Interop.IPropertyPage  
        'Summary: Return a stucture describing your property page.  
        ....   
        Public Sub GetPageInfo(ByVal pPageInfo As Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO())  
            Dim info As PROPPAGEINFO = New PROPPAGEINFO()  
            info.cb = CUInt(Marshal.SizeOf(GetType(PROPPAGEINFO)))  
            info.dwHelpContext = 0  
            info.pszDocString = Nothing  
            info.pszHelpFile = Nothing  
            info.pszTitle = "Deployment" 'Assign tab name  
            info.SIZE.cx = Me.Size.Width  
            info.SIZE.cy = Me.Size.Height  
            If Not pPageInfo Is Nothing AndAlso pPageInfo.Length > 0 Then  
                pPageInfo(0) = info  
            End If  
        End Sub  
    End Class  
    ```  
  
    ```c#  
    class DeployPropertyPage : Form, Microsoft.VisualStudio.OLE.Interop.IPropertyPage  
    {  
        . . . .   
        //Summary: Return a stucture describing your property page.  
        public void GetPageInfo(Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO[] pPageInfo)  
        {  
            PROPPAGEINFO info = new PROPPAGEINFO();  
            info.cb = (uint)Marshal.SizeOf(typeof(PROPPAGEINFO));  
            info.dwHelpContext = 0;  
            info.pszDocString = null;  
            info.pszHelpFile = null;  
            info.pszTitle = "Deployment";  //Assign tab name  
            info.SIZE.cx = this.Size.Width;  
            info.SIZE.cy = this.Size.Height;  
            if (pPageInfo != null && pPageInfo.Length > 0)  
                pPageInfo[0] = info;  
        }  
    }  
    ```  
  
2.  Registrieren Sie die neue Eigenschaftenseite.  
  
    ```vb#  
    <MSVSIP.ProvideObject(GetType(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)>  
    ```  
  
    ```c#  
    [MSVSIP.ProvideObject(typeof(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)]  
    ```  
  
3.  Überschreiben Sie die `GetProperty(uint itemId, int propId, out object property)`\-Methode, um Eigenschaftenseiten zu filtern, verwenden Sie eine `clsids` Liste, und fügen Sie eine neue Eigenschaftenseite hinzufügen.  
  
    ```vb#  
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer  
        'Use propId to filter configuration-dependent property pages.  
        Select Case propId  
            ....   
            case CInt(Fix(__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList)):  
                'Get a semicolon-delimited list of clsids of the configuration-dependent property pages.  
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))  
                'Add the Deployment property page.  
                [property] &= ";"c + GetType(DeployPropertyPage).GUID.ToString("B")  
        End Select  
            ....   
            Return MyBase.GetProperty(itemId, propId, [property])  
    End Function  
    ```  
  
    ```c#  
    protected override int GetProperty(uint itemId, int propId, out object property)  
    {  
        //Use propId to filter configuration-dependent property pages.  
        switch (propId)  
        {  
            . . . .  
            case (int)__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList:  
                {  
                    //Get a semicolon-delimited list of clsids of the configuration-dependent property pages.  
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));  
                    //Add the Deployment property page.  
                    property += ';' + typeof(DeployPropertyPage).GUID.ToString("B");  
                }  
         }  
            . . . .  
        return base.GetProperty(itemId, propId, out property);  
    }  
    ```  
  
> [!NOTE]
>  Alle Codebeispiele in diesem Thema bereitgestellt werden, sind Teil eines umfangreicheren Beispiels, [VSSDK\-Beispiele](../misc/vssdk-samples.md).  
  
## Siehe auch  
 [Projekt\-Untertypen](../extensibility/internals/project-subtypes.md)