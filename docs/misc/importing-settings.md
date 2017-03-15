---
title: "Importieren von Einstellungen | Microsoft Docs"
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
  - "Benutzereinstellungen [Visual Studio SDK], Importieren mithilfe des Managed Package Frameworks"
  - "IDE-Einstellungen, Importieren mithilfe des Managed Package Frameworks"
  - "IDE, Importieren von Einstellungen mithilfe des Managed Package Frameworks"
  - "Managed Package Framework, Importieren von Umgebungseinstellungen"
ms.assetid: 943f9a5b-c5a5-45ce-a5a9-8d4c02f15577
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# Importieren von Einstellungen
In der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE \(integrierte Entwicklungsumgebung\) werden die Klassen, die die <xref:Microsoft.VisualStudio.Shell.IProfileManager>\-Schnittstelle implementieren und registriert sind, dazu verwendet, eine VSPackage\-Implementierung zu unterstützen. Diese Implementierung wird dazu verwendet, den Status eines VSPackage abzurufen.  
  
 Weil die IDE die Klasse instanziiert, die die <xref:Microsoft.VisualStudio.Shell.IProfileManager>\-Schnittstelle implementiert, damit die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Einstellungen unterstützt werden, sollte die <xref:Microsoft.VisualStudio.Shell.IProfileManager>Schnittstelle in einer unabhängigen Klasse implementiert werden.  
  
> [!NOTE]
>  Implementieren Sie <xref:Microsoft.VisualStudio.Shell.IProfileManager> nicht in der Klasse, die <xref:Microsoft.VisualStudio.Shell.Package> implementiert.  
  
### So implementieren Sie den Export von Einstellungen  
  
1.  Deklarieren Sie die Klasse, die die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Einstellungen implementiert.  
  
     Deklarieren Sie eine Klasse zur Implementierung von <xref:Microsoft.VisualStudio.Shell.IProfileManager>, und weisen Sie ihr eine `GUID` zu.  
  
    > [!NOTE]
    >  Eine Klasse, die die <xref:Microsoft.VisualStudio.Shell.IProfileManager>\-Schnittstelle implementiert, muss die <xref:System.ComponentModel.IComponent>\-Schnittstelle implementieren. Dies lässt sich erreichen, indem die Klasse aus der <xref:System.ComponentModel.Component>\-Klasse abgeleitet wird.  
  
     Zum Beispiel:  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  Vergewissern Sie sich, dass die Klasse, die die Einstellungen implementiert, Statusdaten vom Datenträger abruft.  
  
     Dieser Schritt wird ausgeführt, indem die <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A>\-Methode implementiert wird.  
  
     Die genauen Informationen, die beibehalten werden müssen, und die Art und Weise, wie diese Informationen aus dem VSPackage abgerufen und gemarshallt werden, sind für jedes VSPackage unterschiedlich.  
  
     Unabhängig von den Informationen, die vom VSPackage beibehalten werden müssen, muss die Klasse, die <xref:Microsoft.VisualStudio.Shell.IProfileManager> implementiert, die bereitgestellte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>\-Schnittstelle verwenden, um Daten aus der Einstellungendatei abzurufen.  
  
     Üblicherweise, wie im folgenden Beispiel, überprüft <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> auch die abgerufenen Daten und aktualisiert den Status des VSPackage.  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        Dim value As String   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        reader.ReadSettingString("PbrsShowDesc", value)   
        If value Is Nothing OrElse value = "" Then   
            reader.ReportError("Unable to Help Visibility Setting")   
        Else   
            myState.HelpVisible = Not value.Equals("0")   
        End If   
        reader.ReadSettingString("PbrsAlpha", value)   
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
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
    if (mySvc != null){  
      string value;  
      StateObject myState = mySvc.MyPackage.packageState;  
      reader.ReadSettingString("PbrsShowDesc", out value);  
      if (value == null || value == ""){  
          reader.ReportError("Unable to Help Visibility Setting");  
      }else{  
          myState.HelpVisible = !value.Equals("0");  
      }  
      reader.ReadSettingString("PbrsAlpha", out value);  
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
    ```  
  
     Implementierungsdetails:  
  
    -   Fehler werden dem Benutzer interaktiv über die IDE berichtet, indem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A>\-Methode der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>\-Schnittstelle verwendet wird:  
  
        ```vb#  
        reader.ReadSettingString("PbrsAlpha", value)   
        If value Is Nothing OrElse value = "" Then   
            reader.ReportError("Unable to Retrieve Sort Value")   
        End If  
        ```  
  
        ```c#  
          reader.ReadSettingString("PbrsAlpha", out value);  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }  
        ```  
  
    -   Bevor gespeicherte Einstellungen tatsächlich abgerufen werden, sollte eine Implementierung der <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A>\-Methode die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A>\-Methode verwenden, um sicherzustellen, dass die Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], die die gespeicherten Einstellungen exportiert, unterstützt wird.  
  
         Im folgenden Beispiel überprüft die Implementierung, ob Einstellungen von einer Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mit der Hauptversionsnummer `m_supportVer`, erstellt wurden. Ist dies nicht der Fall, signalisiert die Implementierung einen Fehler.  
  
        ```vb#  
        If pnMajor <> m_supportVer Then   
            reader.ReportError("Unsupported Version")   
        End If  
        ```  
  
        ```c#  
        if (pnMajor != m_supportVer){  
          reader.ReportError("Unsupported Version");  
        }  
        ```  
  
    -   Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Einstellungsdatei unterstützt zufälligen Datenzugriff, sodass die Reihenfolge der Vorgänge zum Lesen und Schreiben von Einstellungen ohne Bedeutung ist. Im folgenden Beispiel ist die Reihenfolge der Schreibvorgänge in der Implementierung der <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>\-Methode umgekehrt zu den Lesevorgängen in der <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A>\-Methode.  
  
    -   Der Wert des `pszSettingName`\-Arguments, das einer Methode der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>\-Schnittstelle bereitgestellt wird, muss jedes in einer Einstellungskategorie gespeicherte Datenelement eindeutig identifizieren.  
  
        > [!NOTE]
        >  Namen müssen nur im Bereich der implementierenden Klasse eindeutig sein, da die IDE die GUID der Klasse, die die Einstellungen implementiert, sowie den Wert von `pszSettingName` verwendet, um jede gespeicherte Einstellung zu identifizieren. Werden mehrere <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>\-Methoden mit dem gleichen Wert von `pszSettingName` aufgerufen, wird der ursprüngliche Wert in der Datei außer Kraft gesetzt.  
  
3.  Stellen Sie die Kohärenz zwischen VSPackage\-Status und lokal gespeicherten oder zwischengespeicherten Einstellungen sicher.  
  
     Dieser Schritt wird normalerweise während der Implementierung der <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A>\-Methode ausgeführt \(wie im folgenden Beispiel zu sehen ist\). Die Details dieses Schritts gelten speziell für ein VSPackage und können Folgendes bedingen: Der Status des VSPackage wird aus der Automatisierung abgerufen, das VSPackage wird abgefragt, und es werden Registrierungsschlüssel festgelegt.  
  
    > [!NOTE]
    >  Die <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>\-Methode sollte die Informationen, die durch die <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A>\-Methode gespeichert wurden, abrufen, wenn die <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>\-Methode durch die IDE bei ihrer Initialisierung des VSPackage aufgerufen wird, das sie unterstützt.  
  
     Im folgenden Beispiel implementiert die Klasse, von der die Einstellungenunterstützung bereitgestellt wird, die <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A>\-Methode, um Folgendes umzusetzen:  
  
    -   Erhalten von Zugriff auf die aktualisierten Statusinformationen des VSPackage  
  
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
  
    -   Verwenden dieser Informationen, um die Registrierungseinstellungen des VSPackage zu aktualisieren.  
  
        ```vb#  
        If mySvc.MyPackage.packageState IsNot Nothing Then   
            Using rootKey   
                Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                    Using pbrsKey   
                        DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                    End Using   
                End Using   
            End Using   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.packageState != null) {  
          using (rootKey) {  
            using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
              using (pbrsKey) {  
                ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
              }  
            }  
          }  
        }  
        ```  
  
    -   > [!NOTE]
        >  Die Verteilung der Arbeit zwischen den Methoden <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> und <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> hängt von der Implementierung ab und ist einigermaßen willkürlich. Beispielsweise könnte die Implementierung neu geschrieben werden, sodass die <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>\-Methode als leere Implementierung vorliegt und alle Registrierungs\- und Statusabfragen in der <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>\-Methode ausgeführt werden.  
  
4.  Registrieren Sie die Klasse, die die Einstellungen implementiert, damit Unterstützung für ein VSPackage bereitgestellt wird.  
  
     Wenden Sie eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> an, die durch Verwenden des <xref:System.Type>\-Objekts der Klasse erstellt wurde, die <xref:Microsoft.VisualStudio.Shell.IProfileManager> für die <xref:Microsoft.VisualStudio.Shell.Package>\-Implementierung implementiert.  
  
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
  
     In diesem Fall wird die IDE von dem Attribut informiert, dass die `MyPackageProfileManager`\-Klasse eine Einstellungenimplementierung für die `MyPackage`\-Klasse bereitstellt. Der Punkt für benutzerdefinierte Einstellungen wird in der Registrierung unter „HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\UserSettings\\CoreUI\_MyPackage“ erstellt, wobei *\<Version\>* die Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist, z. B. 8.0.  
  
     Weitere Informationen finden Sie unter [Unterstützung für Benutzereinstellungen](../extensibility/internals/support-for-user-settings.md) und unter <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Beispiel  
 Im folgenden Beispiel wird <xref:Microsoft.VisualStudio.Shell.IProfileManager> für eine Klasse implementiert  
  
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
            ' First check if we are getting data from the correct major version.   
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
      // First check if we are getting data from the correct major version.   
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
 [Exportieren von Einstellungen](../misc/exporting-settings.md)   
 [Unterstützung für Benutzereinstellungen](../extensibility/internals/support-for-user-settings.md)