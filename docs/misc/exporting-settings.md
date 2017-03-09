---
title: "Exportieren von Einstellungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE, Exportieren von Einstellungen mithilfe des verwalteten Paketframeworks"
  - "Verwaltetes Paketframework, Umgebungseinstellungen exportieren "
  - "Benutzereinstellungen [Visual Studio SDK], mithilfe des verwalteten Paketframeworks exportieren"
  - "IDE-Einstellungen, mithilfe des verwalteten Paketframeworks exportieren"
ms.assetid: cb3ddb38-4e75-4f05-a83a-8396345bc36c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Exportieren von Einstellungen
Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung \(IDE\) <xref:Microsoft.VisualStudio.Shell.IProfileManager>\-Klassen, die die Schnittstelle implementieren und \- Klassen, die als Unterstützung einer angegebenen VSPackage\-Implementierung, um den Zustand von VSPackages zu speichern registriert werden.  
  
 Da die IDE die Klasse instanziiert, die die <xref:Microsoft.VisualStudio.Shell.IProfileManager>\-Schnittstelle implementiert, um die Einstellungen zu unterstützen, sollte <xref:Microsoft.VisualStudio.Shell.IProfileManager> in einer unabhängigen Klasse implementiert werden.  
  
> [!NOTE]
>  Implementieren Sie nicht <xref:Microsoft.VisualStudio.Shell.IProfileManager> für die Klasse, die <xref:Microsoft.VisualStudio.Shell.Package>implementiert.  
  
### So implementieren Sie den Export von Einstellungen  
  
1.  Deklarieren Sie die Klasse, die die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Einstellungen implementiert.  
  
     Deklarieren Sie eine Klasse als Implementieren der <xref:Microsoft.VisualStudio.Shell.IProfileManager>\-Schnittstelle und stellen Sie sie mit einer GUID.  
  
    > [!NOTE]
    >  Klassen, die <xref:Microsoft.VisualStudio.Shell.IProfileManager> implementieren, müssen <xref:System.ComponentModel.IComponent>ebenfalls implementieren.  Dies kann erfolgen, indem die Klasse von <xref:System.ComponentModel.Component>berechnet.  
  
     Beispiele:  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  Stellen Sie sicher, dass die Klasse, die die Einstellungen Zustandsinformationen richtige implementiert, erhält.  Dieses Verfahren ist spezifisch für jeden VSPackages und schließt möglicherweise Zustand zum Abrufen von der Automatisierung, fragt Registrierungsschlüssel ab oder fragt ein VSPackage ab.  
  
     Normalerweise, wie im folgenden Beispiel, verwenden Sie die Implementierung der <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>\-Methode, um zu prüfen und der Phase VSPackage\-Zustandsinformationen.  
  
    > [!NOTE]
    >  Die <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>\-Methode wird auch von der IDE aufgerufen, wenn er ein VSPackage initialisiert, die diese unterstützt.  
  
     In diesem Fall wird die Implementierung dieser Methode <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> der Dinge:  
  
    -   Erhält Zugriff auf die Zustandsinformationen in der aktuellen Konfiguration VSPackages und Konfigurationsinformationen, die in der Registrierung gespeichert werden.  
  
        ```vb#  
        Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
        Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
        Dim rootKey As RegistryKey = package.UserRegistryRoot  
        ```  
  
        ```c#  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        Package package = GetService(typeof(Package)) as Package;  
        RegistryKey rootKey = package.UserRegistryRoot;  
        ```  
  
    -   Abhängig von dem Wert, der von der `MakeCurrentSettingTheDefault` VSPackages Methode zurückgegeben wird, aktualisiert sie entweder die Registrierungseinstellungen, indem der aktuellen VSPackage\-Zustand oder den Zustand verwendet, indem die Registrierungseinstellungen verwendet.  
  
        ```vb#  
        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
        Else   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
        }else{  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
        }  
        ```  
  
         Der Einfachheit halber in diesem Beispiel, es sei denn, die `MakeCurrentSettingsTheDefault`\-Methode `true`zurückgibt, wird der aktuelle Status immer auf den Standardwert zurückgesetzt, der in der Registrierung gespeichert wird.  
  
3.  Stellen Sie sicher, dass die Klasse, die die Einstellungen der Implementierung den Zustand auch auf dem Datenträger beibehalten wird.  
  
     Das eigentliche Schreiben von Zustandsinformationen zum Festlegen datenträgerdatei muss durch die Klassenimplementierung der <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>\-Methode immer ausgeführt werden.  Die spezifischen Einstellungen eines Datenvorgangs werden, hängt von der Implementierung ab.  
  
     Allerdings muss die Klasse erhalten Zugriff auf die Zustandsinformationen und über die angegebene <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>\-Schnittstelle verwenden, um Daten in die Datei mit Einstellungen zu speichern.  
  
     Normalerweise, wie im folgenden Beispiel überprüft die Implementierung der Methode nicht <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> Zustandsinformationen.  Die Validierung wird in der <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>\-Methode ausgeführt.  Stattdessen ruft die Implementierung lediglich Zugriff auf die Zustandsinformationen und schreibt es in diesem Fall als Zeichenfolgendaten.  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        ' Information is stored in a StateObject   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
        writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
    End If  
  
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
    if (mySvc != null) {  
      // Information is stored in a StateObject  
      StateObject myState = mySvc.MyPackage.packageState;  
     writer.WriteSettingString(   
                                "PbrsAlpha",   
                                (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
      writer.WriteSettingString(   
                                "PbrsShowDesc",   
                                (myState.HelpVisible ? "1" : "0"));  
    }  
    ```  
  
     Implementierungsdetails lauten wie folgt:  
  
    -   Zusätzlich zu den Daten, die explizit geschrieben werden und die Implementierung der Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> transparent, speichert die Einstellungen auch APIs [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Versionsinformationen.  Daher Einstellungen gespeichert kann für die Version der IDE verglichen werden, das sie während der Einstellungen einfuhr generiert hat.  
  
    -   Der Wert des Arguments `pszSettingName` , das auf eine Methode der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>\-Schnittstelle angegeben wird, muss jedes Datenelement eindeutig bezeichnen, das in eine Einstellungskategorie gespeichert wird.  
  
        > [!NOTE]
        >  Namen müssen innerhalb des Bereichs der implementierenden Klasse lediglich eindeutig sein.  Die IDE verwendet die GUID der Klasse, die die Einstellungen und den Wert `pszSettingName` implementiert, um jede gespeicherte Einstellung zu identifizieren.  Wenn mehr als eine Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> , das denselben Wert haben, `pszSettingName` aufgerufen werden, wird der ursprüngliche Wert in der Einstellungsdatei überschrieben.  
  
    -   Die Einstellungsdatei zufälligen Datenzugriff unterstützt. Daher ist die Reihenfolge von Lese\- und Schreibvorgängen nicht von Bedeutung.  Im folgenden Beispiel ist die Reihenfolge der Vorgänge Writer in der Implementierung der <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>\-Methode Umkehrung der Lesevorgänge in der <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A>\-Methode.  
  
    -   Wenn die Implementierung in Karteninformationen einem der vier unterstützten Formaten kann, gibt es keine Beschränkung auf, wie viel oder dem Typ der Daten geschrieben werden kann.  
  
        > [!NOTE]
        >  Die Arbeitsteilung zwischen <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> und den <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>\-Methode hängt von der Implementierung ab und ist ein wenig beliebigen.  Zum Beispiel kann die Implementierung umgeschrieben werden, indem Sie eine leere Implementierung der <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>\-Methode und Übernehmen aller Registrierungs\- und das Feld Status <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>\-Methode in der Abfrage ausführen.  
  
4.  Registrieren Sie die Einstellungen, die Klasse implementieren, z. B. Unterstützung VSPackage gewährend.  
  
     Wenden Sie eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> , die erstellt wird, indem <xref:System.Type> der Klasse verwendet, die für die Implementierung <xref:Microsoft.VisualStudio.Shell.IProfileManager> VSPackages <xref:Microsoft.VisualStudio.Shell.Package> implementiert.  
  
    ```vb#  
    <ProvideProfile(GetType(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, False)> _   
    <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Class MyPackage   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
    [ProvideProfile(typeof(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, false)]  
    [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    class MyPackage: Package   
    ```  
  
     In diesem Fall teilt das Attribut über die IDE, dass die `MyPackageProfileManager`\-Klasse eine Implementierung der Einstellungen zur `MyPackage`\-Klasse bereitstellt.  Der benutzerdefinierte Einstellungs\-Punkt in der Registrierung wird unter HKLM \\ Software \\ Microsoft \\ VisualStudio \\*Version*\\ UserSettings \\ CoreUI\_MyPackage erstellt, wobei *Version* die Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]z. B. 10.0 ist.  
  
     Weitere Informationen finden Sie unter [Unterstützung für Benutzereinstellungen](../extensibility/internals/support-for-user-settings.md) und <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Beispiel  
 Im folgenden Beispiel implementiert <xref:Microsoft.VisualStudio.Shell.IProfileManager> für eine Klasse.  
  
```vb#  
Imports System   
Imports System.Runtime.InteropServices   
Imports Microsoft.VisualStudio.Shell   
Imports Microsoft.VisualStudio.Shell.Interop   
Imports Microsoft.Win32   
Imports myPackageNameSpace   
Namespace myProfileManagerNameSpace  
  
    <Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class MyPackageProfileManager   
        Inherits System.ComponentModel.Component   
        Implements IProfileManager   
        Friend Const m_supportVer As Integer = 8   
        Public Sub SaveSettingsToXml(ByVal writer As IVsSettingsWriter)   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
            If mySvc IsNot Nothing Then   
                ' Information is stored in a StateObject.   
                Dim myState As StateObject = mySvc.MyPackage.packageState   
                writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
                writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromXml(ByVal reader As IVsSettingsReader)   
  
            Dim pnMajor As Integer, pnMinor As Integer, pnBuild As Integer   
            ' First, check if data is obtained from the correct major version   
            reader.ReadVersion(pnMajor, pnMinor, pnBuild)   
            If pnMajor <> m_supportVer Then   
                reader.ReportError("Unsupported Version")   
            Else   
                Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
                If mySvc IsNot Nothing Then   
                    Dim value As String   
                    Dim myState As StateObject = mySvc.MyPackage.packageState   
                    reader.ReadSettingString("PbrsShowDesc", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Help Visibility Setting")   
                    Else   
                        myState.HelpVisible = Not value.Equals("0")   
                    End If   
                    reader.ReadSettingString("PbrsAlpha", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Retrieve Sort Value")   
                    Else   
                        If Not value.Equals("0") Then   
                            myState.SortState = SortState.Alphabetical   
                        Else   
                            myState.SortState = SortState.Categorized   
                        End If   
                    End If   
                End If   
            End If   
        End Sub   
  
        Public Sub SaveSettingsToStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
  
            If mySvc.MyPackage.packageState IsNot Nothing Then   
                Using rootKey   
                    Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                        Using pbrsKey   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        End Using   
                    End Using   
                End Using   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
            Using rootKey   
                Dim pbrsKey As RegistryKey = rootKey.OpenSubKey(Me.[GetType]().Name)   
                If pbrsKey IsNot Nothing Then   
                    Using pbrsKey   
                        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        Else   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
                        End If   
                    End Using   
                End If   
            End Using   
        End Sub   
    End Class   
End Namespace   
  
Convert C# to VB.NET  
  
```  
  
```c#  
namespace myProfileManagerNameSpace  {  
  
  using System;  
  using System.Runtime.InteropServices;  
  using Microsoft.VisualStudio.Shell;  
  using Microsoft.VisualStudio.Shell.Interop;  
  using Microsoft.Win32;  
  using myPackageNameSpace;  
  
  [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
  internal class MyPackageProfileManager : System.ComponentModel.Component , IProfileManager {  
    internal const int m_supportVer = 8;  
    public void SaveSettingsToXml(IVsSettingsWriter writer) {  
      MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
      if (mySvc != null) {  
        // Information is stored in a StateObject.  
        StateObject myState = mySvc.MyPackage.packageState;  
        writer.WriteSettingString(   
                                  "PbrsAlpha",   
                                  (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
        writer.WriteSettingString(   
                                  "PbrsShowDesc",   
                                  (myState.HelpVisible ? "1" : "0"));  
      }  
    }  
  
    public void LoadSettingsFromXml(IVsSettingsReader reader)  
    {  
  
      int pnMajor, pnMinor, pnBuild;  
      // First, check if data is obtained from the correct major version   
      reader.ReadVersion(pnMajor, pnMinor, pnBuild);  
      if (pnMajor != m_supportVer){  
        reader.ReportError("Unsupported Version");  
      }else{  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        if (mySvc != null){  
          string value;  
          StateObject myState = mySvc.MyPackage.packageState;  
          reader.ReadSettingString("PbrsShowDesc", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Help Visibility Setting");  
          }else{  
            myState.HelpVisible = !value.Equals("0");  
          }  
          reader.ReadSettingString("PbrsAlpha", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }else{  
            if (!value.Equals("0")){  
              myState.SortState = SortState.Alphabetical;  
            }else{  
              myState.SortState = SortState.Categorized;  
            }  
          }  
        }  
      }  
    }  
  
    public void SaveSettingsToStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
  
      if (mySvc.MyPackage.packageState != null) {  
        using (rootKey) {  
          using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
            using (pbrsKey) {  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  
    public void LoadSettingsFromStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
      using (rootKey) {  
        RegistryKey pbrsKey = rootKey.OpenSubKey(this.GetType().Name);  
        if (pbrsKey != null) {  
          using (pbrsKey) {  
            if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }else{  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.IProfileManager>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>   
 [Importieren von Einstellungen](../misc/importing-settings.md)   
 [Unterstützung für Benutzereinstellungen](../extensibility/internals/support-for-user-settings.md)