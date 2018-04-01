---
title: Registrieren eine Vorgängerversion Language "Service1" | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
caps.latest.revision: 22
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2f8edcf34d43311be7406c307a7fea98169712a8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="registering-a-legacy-language-service"></a>Registrieren einen Sprachdienst Legacy
In des managed Package Framework (MPF), wird der Sprachdienst verzichten, durch ein VSPackage (finden Sie unter [VSPackages](../../extensibility/internals/vspackages.md)) und ist mit registrierten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durch Hinzufügen von Registrierungsschlüsseln und Einträge. Dieses Registrierungsprozesses teilweise während der Installation und teilweise zur Laufzeit erfolgt in.  
  
## <a name="register-the-language-service-by-using-attributes"></a>Registrieren des Sprachdiensts mithilfe von Attributen  
 Die folgenden Attribute werden verwendet, um einen Sprachdienst zu registrieren.  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>  
  
 Diese Attribute werden im folgenden erläutert.  
  
### <a name="provideserviceattribute"></a>ProvideServiceAttribute  
 Dieses Attribut wird der Sprachdienst als Dienst registriert.  
  
### <a name="example"></a>Beispiel  
  
```csharp  
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
  
### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute  
 Dieses Attribut wird der Sprachdienst ausdrücklich als einen Sprachdienst registriert. Sie können Sie Optionen festlegen, die die Funktionen angeben, die Ihre Sprachdienst bietet. Das Beispiel zeigt eine Teilmenge der Optionen, die ein Sprachdienst bereitstellen kann. Der vollständige Satz der Sprachoptionen-Dienst werden soll, finden Sie unter <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>.  
  
### <a name="example"></a>Beispiel  
  
```csharp  
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
  
### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute  
 Dieses Attribut ordnet der Sprachdienst mit einer Dateierweiterung an. Wenn eine Datei mit dieser Erweiterung, müssen Sie in jedem Projekt geladen wird ist der Sprachdienst gestartet und verwendet, um den Inhalt der Datei anzuzeigen.  
  
### <a name="example"></a>Beispiel  
  
```csharp  
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
  
### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute  
 Dieses Attribut registriert einen Speicherort, aus welcher, den Code durchgeführte Erweiterung bzw. Ausschnitt Vorlagen abgerufen werden. Diese Informationen werden verwendet, indem Sie die **Code Snippets Browser** und durch den Editor aus, wenn ein Codeausschnitt in der Quelldatei eingefügt wird.  
  
### <a name="example"></a>Beispiel  
  
```csharp  
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
  
### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute  
 Dieses Attribut wird eine Eigenschaftenseite angezeigt werden registriert die **Optionen** im Dialogfeld unter die **Text-Editor** Kategorie. Verwenden Sie eines dieser Attribute für jede Seite für Ihre Sprachdienst angezeigt werden soll. Wenn Ihre Seiten in einer Baumstruktur organisiert werden müssen, verwenden Sie zusätzliche Attribute auf um jedem Knoten der Struktur zu definieren.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt zwei Eigenschaftenseiten **Optionen** und **Einzug**, und ein Knoten, die zweite Eigenschaftenseite enthält.  
  
```csharp  
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
  
## <a name="proffer-the-language-service-at-runtime"></a>Der Sprachdienst zur Laufzeit proffer  
 Wenn die deutschsprachige Paket geladen wird, können Sie erkennen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , dass der Sprachdienst bereit ist. Dazu müssen Sie den Dienst proffering. Dies erfolgt in der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode. Darüber hinaus müssen Sie einen Zeitgeber zu starten, der Language-Dienst während Leerlaufzeiten aufruft, damit Analysieren im Hintergrund ausgeführt werden kann. Diese Leerlaufzeitgeber dient außerdem Dokumenteigenschaften zu aktualisieren, wenn Sie eine durch implementiert haben die <xref:Microsoft.VisualStudio.Package.DocumentProperties> Klasse. Um einen Zeitgeber zu unterstützen, muss Ihr Paket implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> Schnittstelle (nur die <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> Methode muss vollständig implementiert werden; die restlichen Methoden können Standardwerte zurückgeben).  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt einen normalen Ansatz zum proffering eines Diensts und ein Leerlaufzeitgeber bereitstellt.  
  
```csharp  
  
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