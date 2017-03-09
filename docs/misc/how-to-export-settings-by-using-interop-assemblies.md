---
title: "Gewusst wie: Exportieren von Einstellungen mithilfe von Interop-Assemblys | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE-Einstellungen, Exportieren mithilfe von Interop-Assemblys"
  - "Benutzereinstellungen [Visual Studio SDK], Exportieren mithilfe von Interop-Assemblys"
  - "IDE, Exportieren von Einstellungen mithilfe von Interop-Assemblys"
ms.assetid: d470d4f9-3006-40c3-99db-21abcd5003b8
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# Gewusst wie: Exportieren von Einstellungen mithilfe von Interop-Assemblys
Ein VSPackage kann Einstellungen aus der integrierten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Entwicklungsumgebung \(IDE\) exportieren. Die IDE verwendet eine VSPackage\-Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>\-Schnittstelle. Wenn das Paket auch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>\-Schnittstelle bereitstellt, wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>\-Schnittstelle verwendet, um zu bestimmen, wie die VSPackage\-Konfiguration gespeichert wird.  
  
> [!NOTE]
>  Das verwaltete Paketframework \(Managed Package Framework, MPF\) stellt eine Reihe verwalteter Klassen bereit, um die Erstellung von Visual Studio\-Erweiterungen zu erleichtern. Informationen zum Ausführen dieser Aufgabe mithilfe des verwalteten Paketframeworks finden Sie unter [Exportieren von Einstellungen](../misc/exporting-settings.md).  
  
### So implementieren Sie den Export von Einstellungen in einem VSPackage  
  
1.  Implementieren Sie grundlegende Unterstützung für den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Einstellungsmechanismus.  
  
    -   Registrieren Sie das VSPackage als Unterstützung für den Einstellungsmechanismus, indem Sie einen oder mehrere benutzerdefinierte Einstellungspunkte definieren.  
  
         Weitere Informationen finden Sie unter [Unterstützung für Benutzereinstellungen](../extensibility/internals/support-for-user-settings.md).  
  
    -   Deklarieren Sie die Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> durch das VSPackage. Falls gewünscht, kann das VSPackage auch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>\-Schnittstelle implementieren. Zum Beispiel:  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   Stellen Sie sicher, dass die VSPackage\-Implementierung der <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>\-Methode eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>\-Schnittstelle bereitstellt, wenn sie mit `IID_IVsUserSettings` aufgerufen wird.  
  
         Optional kann `QueryInterface` beim Aufruf über die `IID_IVsUserSettingsQuery`\-Schnittstelle eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>\-Schnittstelle bereitstellen.  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  Benachrichtigen Sie die IDE optional über die Notwendigkeit, eine bestimmte Einstellung zu exportieren.  
  
     Ein VSPackage ermöglicht das bedingte Speichern einer Einstellung, die vom benutzerdefinierten Einstellungspunktzustand definiert wird. Es wird z. B. nur dann gespeichert, wenn der Benutzer explizit angibt, dass eine Einstellung gespeichert werden soll.  
  
     In diesem Fall muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>\-Schnittstelle implementiert sein.  
  
     Wenn ein VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> nicht implementiert, werden alle Zustandsinformationen während des Exports von Einstellungen gespeichert.  
  
     Ein VSPackage kann mehrere benutzerdefinierte Einstellungspunkte \(Einstellungskategorie\) unterstützen. Die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery.NeedExport%2A>\-Methode muss die GUID des bereitgestellten benutzerdefinierten Einstellungspunkts oder das Argument der Einstellungskategorie überprüfen, um zu bestimmen, ob eine bestimmte Gruppe von Einstellungen gespeichert werden muss.  
  
     Im folgenden Beispiel erfordert das VSPackage, dass der Befehlsleistenzustand immer gespeichert wird, der Schlüsselbindungszustand aber nur dann gespeichert wird, wenn ein Flag festgelegt wurde.  
  
3.  Schreiben Sie Einstellungsdaten in die Einstellungsdatei.  
  
     Um das Exportieren von Einstellungen zu unterstützen, muss ein VSPackage immer die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>\-Methode implementieren.  
  
     Die Implementierung muss die von der IDE, der GUID der Kategorie dieses benutzerdefinierten Einstellungspunkts und einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>\-Schnittstelle übergebenen Argumente verarbeiten.  
  
    1.  Ein VSPackage kann mehrere benutzerdefinierte Einstellungspunkte \(Einstellungskategorie\) unterstützen. Im folgenden Beispiel ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>\-Methode eine andere Implementierung für den persistenten Befehlsleistenzustand im Gegensatz zum persistenten Schlüsselbindungszustand auf.  
  
    2.  Ein VSPackage muss die angegebene <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>\-Schnittstelle verwenden, um Daten in die Einstellungsdatei zu speichern.  
  
         `interface IVsSettingsWriter : IUnknown`  
  
         `{`  
  
         `HRESULT WriteSettingString( LPCOLESTR pszSettingName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingLong( LPCOLESTR pszSettingName, long lSettingValue);`  
  
         `HRESULT WriteSettingBoolean( LPCOLESTR pszSettingName, BOOL fSettingValue);`  
  
         `HRESULT WriteSettingBytes( LPCOLESTR pszSettingName, BYTE *pSettingValue, long lDataLength);`  
  
         `HRESULT WriteSettingAttribute( LPCOLESTR pszSettingName, LPCOLESTR pszAttributeName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingXml( IUnknown *pIXMLDOMNode);`  
  
         `HRESULT WriteSettingXmlFromString( LPCOLESTR szXML);`  
  
         `HRESULT ReportError( LPCOLESTR pszError, VSSETTINGSERRORTYPES dwErrorType);`  
  
         `};`  
  
         Der Wert des `pszSettingName`\-Arguments, das einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>\-Schnittstelle bereitgestellt wird, muss jedes in einer Einstellungskategorie gespeicherte Datenelement eindeutig identifizieren.  
  
        > [!NOTE]
        >  Namen müssen innerhalb eines benutzerdefinierten Einstellungspunkts eindeutig sein, da die IDE die GUID und den Wert von `pszSettingName` verwendet, um jede gespeicherte Einstellung zu identifizieren. Werden mehrere <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>\-Methoden mit dem gleichen Wert von `pszSettingName` aufgerufen, wird der ursprüngliche Wert in der Datei außer Kraft gesetzt.  
  
         Die Einstellungsdatei unterstützt zufälligen Datenzugriff. Daher ist die Reihenfolge der Vorgänge zum Lesen und Schreiben von Einstellungen nicht wichtig.  
  
         Dies wird in den Implementierungen des Zustands der Befehlsleisten zum Exportieren und Importieren \(`ExportSettings_CommandBa`r und `ImportSettings_CommandBar`\) im folgenden Beispiel verdeutlicht.  
  
         Wenn die Implementierung Daten in einem der vier unterstützten Formate zuordnen kann, besteht keine Einschränkung dahingehend, wie viele oder welche Art von Daten geschrieben werden können.  
  
        > [!NOTE]
        >  Zusätzlich zu den explizit geschriebenen und für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>\-Implementierung transparenten Daten speichert die Einstellungen\-API auch die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Versionsinformationen. Gespeicherte Einstellungen können mit der Version der IDE verglichen werden, die sie während des Imports der Einstellungen generiert hat.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie Einstellungsdaten importiert und exportiert werden.  
  
```  
// -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export. //    Delegate to the right shell object based on the category GUID. // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to treat import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning, these settings should immediately //             be applied to your personal settings store, //             whether in the registry or the file system. // This write-through cache methodology is essential to to work //             in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether import can be treated as an additive // operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: Before returning, these settings should immediately //             be applied to your personal settings //             store, whether in the registry or the file system. // This write-through cache methodology is essential to allow us //             to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## Siehe auch  
 [Unterstützung für Benutzereinstellungen](../extensibility/internals/support-for-user-settings.md)   
 [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)   
 [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Gewusst wie: Verwenden von Interopassemblys zum Importieren von Einstellungen](../misc/how-to-use-interop-assemblies-to-import-settings.md)