---
title: Registrieren eine Ausdrucksauswertung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a34278ecca071c31e62ff4e405e9d7ada112d425
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="registering-an-expression-evaluator"></a>Registrieren eine Ausdrucksauswertung
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Die ausdrucksauswertung (EE) muss sich selbst als Klassenfactory mit dem Windows-COM-Umgebung und die Visual Studio registrieren. Ein EE wird als DLL implementiert, damit es in den Adressraum des Debug-Modul (DE) oder die Visual Studio-Adressraums, je nachdem, die welche Entität die EE instanziiert eingefügt werden kann.  
  
## <a name="managed-code-expression-evaluator"></a>Ausdrucksauswertung für verwalteten Code  
 Eine verwaltete Code EE wird als eine Klassenbibliothek, die eine DLL, der sich mit der COM-Umgebung ist, in der Regel durch einen Aufruf an das Programm VSIP gestartet registriert implementiert **regpkg.exe**. Der tatsächliche Prozess des Schreibens der Registrierungsschlüssel für die COM-Umgebung wird automatisch durchgeführt.  
  
 Eine Methode der Hauptklasse wird markiert, mit der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, gibt an, dass diese Methode empfiehlt sich, die aufgerufen werden, wenn die DLL mit COM registriert wird Diese häufig aufgerufene Registrierungsmethode `RegisterClass`, führt die Aufgabe der Registrierung der DLL mit Visual Studio. Ein entsprechendes `UnregisterClass` (gekennzeichnet mit der <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), macht die Auswirkungen der `RegisterClass` Wenn die DLL deinstalliert wird.  
  
 Die gleichen Registrierungseinträge erfolgen wie für eine EE in nicht verwaltetem Code geschrieben; der einzige Unterschied ist, dass es keine Hilfsfunktion wie z. B. `SetEEMetric` die Arbeit für Sie ausführen. Ein Beispiel für diese Registrierung/Aufhebung sieht wie folgt:  
  
### <a name="example"></a>Beispiel  
 Diese Funktion wird gezeigt, wie eine verwaltete Code EE registriert, und selbst mit Visual Studio hebt die Registrierung.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code-expression-evaluator"></a>Ausdrucksauswertung von nicht verwaltetem Code  
 Die EE-DLL implementiert die `DllRegisterServer` Funktion selbst die COM-Umgebung sowie Visual Studio registrieren.  
  
> [!NOTE]
>  In der Datei dllentry.cpp befindet sich im die VSIP-Installation unter EnVSDK\MyCPkgs\MyCEE, kann der MyCEE Code Beispielcode Registrierung gefunden werden.  
  
### <a name="dll-server-process"></a>DLL-Server-Prozess  
 Wenn die EE DLL-Server zu registrieren:  
  
1.  Registriert die Klassenfactory `CLSID` gemäß den normalen COM-Konventionen.  
  
2.  Ruft die Hilfsfunktion `SetEEMetric` mit Visual Studio die EE Metriken, die in der folgenden Tabelle aufgeführten registrieren. Die Funktion `SetEEMetric` und die unten angegebenen Metriken sind Teil der dbgmetric.lib-Bibliothek. Finden Sie unter [SDK-Hilfsprogramme zum Debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Details.  
  
    |Metrik|Beschreibung|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` der Factory EE-Klasse|  
    |`metricName`|Name des der EE als einer darstellbaren Zeichenfolge|  
    |`metricLanguage`|Der Name der Sprache, die die EE ist auswerten soll|  
    |`metricEngine`|`GUID`s der Debugmodule (DE), die mit diesem EE arbeiten|  
  
    > [!NOTE]
    >  Die `metricLanguage``GUID` identifiziert die Sprache von Namen, aber es ist die `guidLang` Argument `SetEEMetric` auswählt, die Sprache. Wenn der Compiler die Debuginformationsdatei generiert, sollten die entsprechenden schreiben `guidLang` , damit die DE weiß, welche EE verwenden. Die DE fordert die Symbol-Anbieter in der Regel für diese Sprache `GUID`, der in der Debug-Informationsdatei gespeichert ist.  
  
3.  Registriert bei Visual Studio durch Erstellen von Schlüsseln unter HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, wobei *X.Y* ist die Version von Visual Studio zu registrieren.  
  
### <a name="example"></a>Beispiel  
 Diese Funktion wird gezeigt, wie eine nicht verwaltete Code (C++) EE registriert, und selbst mit Visual Studio hebt die Registrierung.  
  
```cpp  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [SDK-Hilfsprogramme für das Debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)