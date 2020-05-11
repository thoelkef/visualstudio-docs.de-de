---
title: Registrieren eines Legacy Language Service1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91776382fff1818986049558c9d86e8fce4d0dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705904"
---
# <a name="registering-a-legacy-language-service"></a>Registrieren eines Legacysprachdiensts
Im Managed Package Framework (MPF) wird der Sprachdienst von einem VSPackage angeboten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (siehe [VSPackages](../../extensibility/internals/vspackages.md)) und durch Hinzufügen von Registrierungsschlüsseln und Einträgen registriert. Dieser Registrierungsprozess erfolgt teils während der Installation und teilweise zur Laufzeit.

## <a name="register-the-language-service-by-using-attributes"></a>Registrieren des Sprachdienstes mithilfe von Attributen
 Die folgenden Attribute werden zum Registrieren eines Sprachdienstes verwendet.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Diese Attribute werden im Folgenden erläutert.

### <a name="provideserviceattribute"></a>ProvideServiceAttribute
 Dieses Attribut registriert Ihren Sprachdienst als Dienst.

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
 Dieses Attribut registriert Ihren Sprachdienst speziell als Sprachdienst. Sie können Optionen festlegen, die die Funktionen angeben, die Ihr Sprachdienst bietet. Das Beispiel zeigt eine Teilmenge der Optionen, die ein Sprachdienst bereitstellen kann. Den vollständigen Satz an Sprachdienstoptionen finden Sie unter <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>.

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
 Dieses Attribut ordnet Ihren Sprachdienst einer Dateierweiterung zu. Immer wenn eine Datei mit dieser Erweiterung geladen wird, wird in jedem Projekt der Sprachdienst gestartet und zum Anzeigen des Inhalts der Datei verwendet.

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
 Dieses Attribut registriert einen Speicherort, von dem Codeerweiterungs- oder Ausschnittvorlagen abgerufen werden. Diese Informationen werden vom **Code Snippets Browser** und vom Editor verwendet, wenn ein Codeausschnitt in die Quelldatei eingefügt wird.

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
 Dieses Attribut registriert eine Eigenschaftenseite, die im Dialogfeld **Optionen** unter der Kategorie **Texteditor** angezeigt werden soll. Verwenden Sie eines dieser Attribute für jede Seite, die für Ihren Sprachdienst angezeigt werden soll. Wenn Sie Ihre Seiten in einer Baumstruktur organisieren müssen, verwenden Sie zusätzliche Attribute, um jeden Knoten der Struktur zu definieren.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt zwei Eigenschaftenseiten, **Optionen** und **Einzug**, und einen Knoten, der die zweite Eigenschaftenseite enthält.

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

## <a name="proffer-the-language-service-at-run-time"></a>Bieten Sie den Sprachdienst zur Laufzeit
 Wenn Ihr Sprachpaket geladen ist, müssen Sie mitteilen, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dass Ihr Sprachdienst bereit ist. Sie tun dies, indem Sie den Service anbieten. Dies geschieht <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> in der Methode. Darüber hinaus müssen Sie einen Timer starten, der Ihren Sprachdienst während Leerlaufzeiten aufruft, damit die Hintergrundanalyse durchgeführt werden kann. Dieser Leerlauf-Timer wird auch verwendet, um Dokumenteigenschaften zu aktualisieren, wenn Sie über die <xref:Microsoft.VisualStudio.Package.DocumentProperties> Klasse implementiert haben. Um einen Timer zu unterstützen, muss <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> Ihr Paket <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> die Schnittstelle implementieren (nur die Methode muss vollständig implementiert werden; die verbleibenden Methoden können Standardwerte zurückgeben).

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt einen typischen Ansatz zum Anbieten eines Dienstes und zum Bereitstellen eines Leerlaufzeitgebers.

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
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal |
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
