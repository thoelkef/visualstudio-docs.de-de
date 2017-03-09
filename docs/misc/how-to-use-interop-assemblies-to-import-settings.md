---
title: "Gewusst wie: Verwenden von Interopassemblys zum Importieren von Einstellungen | Microsoft Docs"
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
  - "IDE-Einstellungen, Importieren mithilfe von Interopassemblys"
  - "IDE, Importieren von Einstellungen mithilfe von Interopassemblys"
  - "Benutzereinstellungen [Visual Studio SDK], Importieren mithilfe von Interopassemblys"
ms.assetid: 8a43dbe2-fdc0-471b-8235-3f489b77db0f
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# Gewusst wie: Verwenden von Interopassemblys zum Importieren von Einstellungen
Ein VSPackage kann Einstellungen aus der integrierten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Entwicklungsumgebung \(Integrated Development Environment, IDE\) importieren. Die IDE ermittelt anhand der VSPackage\-Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>\-Schnittstelle, wie die VSPackage\-Konfiguration abgerufen werden soll.  
  
> [!NOTE]
>  Das Managed Package Framework \(MPF\) stellt eine Reihe verwalteter Klassen bereit, um die Erstellung von Visual Studio\-Erweiterungen zu erleichtern. Informationen zum Ausführen dieser Aufgabe mithilfe von MPF finden Sie unter [Importieren von Einstellungen](../misc/importing-settings.md).  
  
### So implementieren Sie den Import von Einstellungen in einem VSPackage  
  
1.  Implementieren Sie grundlegende Unterstützung für den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Einstellungsmechanismus.  
  
    -   Registrieren Sie das VSPackage als Unterstützung für den Einstellungsmechanismus, indem Sie mindestens einen benutzerdefinierten Einstellungspunkt definieren.  
  
         Weitere Informationen finden Sie unter [Unterstützung für Benutzereinstellungen](../extensibility/internals/support-for-user-settings.md).  
  
    -   Deklarieren Sie die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>\-Schnittstelle durch das VSPackage. Beispiel:  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   Stellen Sie sicher, dass die VSPackage\-Implementierung der <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>\-Methode eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>\-Schnittstelle bereitstellt, wenn sie mit `IID_IVsUserSettings` aufgerufen wird. Zum Beispiel:  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  Rufen Sie Einstellungsinformationen ab.  
  
     Damit der Abruf von Einstellungsinformationen unterstützt wird, muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>\-Methode von einem VSPackage implementiert werden.  
  
     Um Daten zu lesen, muss eine VSPackage\-Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>\-Schnittstelle die ersten beiden von der IDE übergebenen Argumente verwenden: die GUID der Kategorie dieses benutzerdefinierten Einstellungspunkts und eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>\-Schnittstelle.  
  
    1.  Eine VSPackage\-Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>\-Methode muss die übergebene Kategorie\-GUID überprüfen und den passenden Mechanismus für den Abrufzustand auswählen.  
  
         Im folgenden Beispiel ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>\-Methode beim Abruf des Befehlsleistenzustands eine andere Implementierung auf als beim Abruf des Schlüsselbindungszustands.  
  
    2.  Ein VSPackage muss die angegebene <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>\-Schnittstelle verwenden, um Daten für die Einstellungsdatei abzurufen.  
  
        > [!NOTE]
        >  Wenn sich die Einstellungsinformationen als Funktion einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Version ändern, muss eine VSPackage\-Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>\-Methode vor dem Lesen der Daten die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A>\-Methode verwenden, um die IDE\-Version zu überprüfen.  
  
         Die Schnittstelle stellt Methoden für das Lesen verschiedener Datentypen aus der Einstellungsdatei bereit.  
  
         `interface IVsSettingsReader : IUnknown`  
  
         `{`  
  
         `HRESULT ReadSettingString(WCHAR *pszSettingName, BSTR *pbstrSettingValue);`  
  
         `HRESULT ReadSettingLong(WCHAR *pszSettingName, long *plSettingValue);`  
  
         `HRESULT ReadSettingBoolean(WCHAR *pszSettingName, BOOL *pfSettingValue);`  
  
         `HRESULT ReadSettingAttribute(LPCOLESTR pszSettingName,LPCOLESTR pszAttributeName, BSTR *pbstrSettingValue);  //Internal use only`  
  
         `HRESULT ReadSettingBytes(WCHAR *pszSettingName, BYTE *pSettingValue, long *plDataLength, long lDataMax);`  
  
         `HRESULT ReadVersion(int *pnMajor, int *pnMinor, int *pnBuild);`  
  
         `HRESULT ReportError(WCHAR *pszError);`  
  
         `};`  
  
     Die Einstellungsdatei unterstützt den zufälligen Datenzugriff, sodass die Reihenfolge der Vorgänge zum Lesen und Schreiben von Einstellungen ohne Bedeutung ist.  
  
     Dies wird durch den Export\- und Import\-Befehlsleistenzustand \(`ExportSettings_CommandBa`r und `ImportSettings_CommandBar`\) der Implementierung im folgenden Beispiel verdeutlicht.  
  
3.  Überprüfen Sie die abgerufenen Daten.  
  
     Die Einstellungsinformationen sind in XML\-Dateien gespeichert, die manuell bearbeitet werden können.  
  
> [!IMPORTANT]
>  Es kann vorkommen, dass auf einem Datenträger gespeicherte Einstellungsinformationen beschädigt sind, dass sie versionsspezifische Einstellungen enthalten oder für böswillige Angriffe missbraucht werden. Die Gültigkeit jedes von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>\-Methode zurückgegebenen Datenelements sollte überprüft werden.  
  
-   Um festzustellen, ob die zum Erstellen der abgerufenen Einstellungen verwendete [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Version unterstützt wird, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A>\-Methode auf, um die Version abzurufen.  
  
-   Damit Benutzer von der IDE benachrichtigt werden, wenn ein importiertes Datenelement ungültig ist, ruft ein VSPackage die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A>\-Methode auf.  
  
1.  Wenden Sie die Einstellungsinformationen an.  
  
    1.  Die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>\-Methode muss den Wert des dritten Arguments berücksichtigen, das von der IDE übergeben wurde. Die unterstützten Werte sind Member der <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>\-Enumeration. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>.  
  
         Im folgenden Beispiel verwendet die Implementierung zum Import von Befehlsleisteneinstellungen \(`ImportSettings_Commandbar`\) den Wert dieses Arguments, um festzustellen, ob Einstellungen zum Überschreiben vorhandener Werte angewendet oder zusätzlich aktualisiert werden sollen.  
  
    2.  Sie müssen eine Write\-Through\-Cachemethode implementieren, wenn Sie importierte Einstellungen anwenden.  
  
         Zustandsinformationen in der Registrierung oder im Dateisystem müssen zur selben Zeit aktualisiert werden, zu der Einstellungen auf die IDE angewendet werden. Dadurch wird sichergestellt, dass die Konfiguration kohärent ist und IDE\-Szenarien mit mehreren Instanzen unterstützt.  
  
2.  Teilen Sie der IDE mit, wie der Import von Einstellungen erfolgen soll.  
  
     Verwenden Sie das zurückgegebene `pfRestartRequired`\-Argument der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>\-Methode, um die IDE darüber zu informieren, ob ein Neustart erforderlich ist, um die importierten Einstellungen anzuwenden.  
  
     Wenn die VSPackage\-Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>\-Methode `true` zurückgibt, wird der Benutzer aufgefordert, die IDE neu zu starten.  
  
## Beispiel  
 Im Beispiel wird veranschaulicht, wie Einstellungsdaten importiert und exportiert werden.  
  
```  
static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export and import //    Delegate to the right shell object based on the category GUID // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether to import as an additive operation or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## Siehe auch  
 [Gewusst wie: Exportieren von Einstellungen mithilfe von Interop\-Assemblys](../misc/how-to-export-settings-by-using-interop-assemblies.md)   
 [Unterstützung für Benutzereinstellungen](../extensibility/internals/support-for-user-settings.md)   
 [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)   
 [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3)