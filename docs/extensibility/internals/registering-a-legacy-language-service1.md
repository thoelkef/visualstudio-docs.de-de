---
title: "Registrieren einer Legacy-Language &quot;Service1&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sprachdienste [Verwaltetes Paketframework], registrieren"
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Registrieren einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In verwalteten Paketframework \(MPF\) wird der Sprachdienst nach einem VSPackage verzichten \(finden Sie unter [VSPackages](../../extensibility/internals/vspackages.md)\) und registriert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Registrierungsschlüssel und\-Einträge hinzufügen. Dieses Registrierungsprozesses wird teilweise während der Installation und teilweise während der Laufzeit durchgeführt.  
  
## Registrieren des Sprachdiensts mithilfe von Attributen  
 Die folgenden Attribute werden zum Registrieren eines Sprachdiensts.  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>  
  
 Diese Attribute werden im folgenden erläutert.  
  
### ProvideServiceAttribute  
 Dieses Attribut wird der Sprachdienst als Dienst registriert.  
  
### Beispiel  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideServiceAttribute(typeof(TestLanguageService),  
                             ServiceName = "Test Language Service")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### ProvideLanguageServiceAttribute  
 Dieses Attribut wird der Sprachdienst speziell als Sprachdienst registriert. Sie können Optionen festlegen, mit denen die Funktionen der Sprachdienst bietet. Das Beispiel zeigt eine Teilmenge der Optionen, die einen Sprachdienst bereitstellen kann. Die vollständige Language Service\-Optionen, finden Sie unter <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>.  
  
### Beispiel  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),  
                             "Test Language",  
                             106,             // resource ID of localized language name  
                             CodeSense = true,             // Supports IntelliSense  
                             RequestStockColors = false,   // Supplies custom colors  
                             EnableCommenting = true,      // Supports commenting out code  
                             EnableAsyncCompletion = true  // Supports background parsing  
                             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### ProvideLanguageExtensionAttribute  
 Dieses Attribut ordnet der Sprachdienst mit der Erweiterung. Wenn eine Datei mit dieser Erweiterung, in jedem Projekt geladen wird der Sprachdienst gestartet und verwendet, um den Inhalt der Datei anzuzeigen.  
  
### Beispiel  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),  
                                       ".Testext")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### ProvideLanguageCodeExpansionAttribute  
 Dieses Attribut registriert einen Speicherort aus, welcher, den Code Erweiterung oder Ausschnitt Vorlagen abgerufen werden. Diese Informationen werden verwendet, indem Sie die **Code Snippets Browser** und durch den Editor aus, wenn ein Codeausschnitt in die Quelldatei eingefügt wird.  
  
### Beispiel  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageCodeExpansionAttribute(  
             typeof(TestLanguageService),  
             "Test Language", // Name of language used as registry key.  
             106,           // Resource ID of localized name of language service.  
             "testlanguage",  // language key used in snippet templates.  
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index  
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +  
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### ProvideLanguageEditorOptionPageAttribute  
 Dieses Attribut registriert eine Eigenschaftenseite in angezeigt werden sollen die **Optionen** im Dialogfeld unter den **Texteditor** Kategorie. Verwenden Sie eines dieser Attribute für jede Seite für Ihren Sprachdienst angezeigt werden soll. Wenn Ihre Seiten in einer Baumstruktur organisiert werden sollen, verwenden Sie zusätzliche Attribute auf um jedem Knoten der Struktur zu definieren.  
  
### Beispiel  
 Dieses Beispiel zeigt zwei Eigenschaftenseiten **Optionen** und **Einzug**, und ein Knoten, der die zweite Eigenschaftenseite enthält.  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Options",      // Registry key name for property page  
             "#242",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Advanced",     // Registry key name for node  
             "#243",         // Localized name of node  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             @"Advanced\Indenting",     // Registry key name for property page  
             "#244",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
## Den Sprachdienst zur Laufzeit proffer  
 Wenn Ihre Sprachpaket geladen wird, muss man [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dass der Sprachdienst bereit ist. Dazu müssen Sie den Dienst proffering. Dies erfolgt in der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode. Darüber hinaus müssen Sie einen Zeitgeber zu starten, der Ihren Language\-Dienst während Leerlaufzeiten aufruft, damit Analysieren im Hintergrund ausgeführt werden kann. Diese Leerlaufzeitgeber dient außerdem zum Dokumenteigenschaften zu aktualisieren, wenn Sie eine über implementiert haben die <xref:Microsoft.VisualStudio.Package.DocumentProperties> Klasse. Um einen Zeitgeber zu unterstützen, muss das Paket implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> Schnittstelle \(nur die <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> Methode vollständig implementiert werden muss; die verbleibenden Methoden können Standardwerte zurückgegeben\).  
  
### Beispiel  
 Dieses Beispiel zeigt einen normalen Ansatz zum proffering eines Diensts und ein Leerlaufzeitgeber angeben.  
  
```c#  
  
using System;  
using System.Runtime.InteropServices;  
using System.ComponentModel.Design;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.OLE.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,  
        AutoOutlining = true,  
        EnableCommenting = true,  
        MatchBraces = true,  
        ShowMatchingBrace = true)]  
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package  
  
    public class TestLanguagePackage : Package, IOleComponent  
    {  
        private uint m_componentID;  
  
        protected override void Initialize()  
        {  
            base.Initialize();  // required  
  
            // Proffer the service.  
            IServiceContainer serviceContainer = this as IServiceContainer;  
            TestLanguageService langService      = new TestLanguageService();  
            langService.SetSite(this);  
            serviceContainer.AddService(typeof(TestLanguageService),  
                                        langService,  
                                        true);  
  
            // Register a timer to call our language service during  
            // idle periods.  
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                       as IOleComponentManager;  
            if (m_componentID == 0 && mgr != null)  
            {  
                OLECRINFO[] crinfo = new OLECRINFO[1];  
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));  
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |  
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;  
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal     |  
                                              (uint)_OLECADVF.olecadvfRedrawOff |  
                                              (uint)_OLECADVF.olecadvfWarningsOff;  
                crinfo[0].uIdleTimeInterval = 1000;  
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);  
            }  
        }  
  
        protected override void Dispose(bool disposing)  
        {  
            if (m_componentID != 0)  
            {  
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                           as IOleComponentManager;  
                if (mgr != null)  
                {  
                    int hr = mgr.FRevokeComponent(m_componentID);  
                }  
                m_componentID = 0;  
            }  
  
            base.Dispose(disposing);  
        }  
  
        #region IOleComponent Members  
  
        public int FDoIdle(uint grfidlef)  
        {  
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;  
            // Use typeof(TestLanguageService) because we need to  
            // reference the GUID for our language service.  
            LanguageService service = GetService(typeof(TestLanguageService))  
                                      as LanguageService;  
            if (service != null)  
            {  
                service.OnIdle(bPeriodic);  
            }  
            return 0;  
        }  
  
        public int FContinueMessageLoop(uint uReason,  
                                        IntPtr pvLoopData,  
                                        MSG[] pMsgPeeked)  
        {  
            return 1;  
        }  
  
        public int FPreTranslateMessage(MSG[] pMsg)  
        {  
            return 0;  
        }  
  
        public int FQueryTerminate(int fPromptUser)  
        {  
            return 1;  
        }  
  
        public int FReserved1(uint dwReserved,  
                              uint message,  
                              IntPtr wParam,  
                              IntPtr lParam)  
        {  
            return 1;  
        }  
  
        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)  
        {  
            return IntPtr.Zero;  
        }  
  
        public void OnActivationChange(IOleComponent pic,  
                                       int fSameComponent,  
                                       OLECRINFO[] pcrinfo,  
                                       int fHostIsActivating,  
                                       OLECHOSTINFO[] pchostinfo,  
                                       uint dwReserved)  
        {  
        }  
  
        public void OnAppActivate(int fActive, uint dwOtherThreadID)  
        {  
        }  
  
        public void OnEnterState(uint uStateID, int fEnter)  
        {  
        }  
  
        public void OnLoseActivation()  
        {  
        }  
  
        public void Terminate()  
        {  
        }  
  
        #endregion  
    }  
}   
```