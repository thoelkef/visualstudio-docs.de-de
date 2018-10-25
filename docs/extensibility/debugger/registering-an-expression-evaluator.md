---
title: Registrieren einer Ausdrucksauswertung | Microsoft-Dokumentation
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
ms.openlocfilehash: 0650a437b4e703405ee9e8a06bfbbf9ac6c5a247
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926786"
---
# <a name="register-an-expression-evaluator"></a>Registrieren einer ausdrucksauswertung
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Die ausdrucksauswertung (EE) muss sich als eine Klassenfactory mit der Windows-COM-Umgebung und die Visual Studio zu registrieren. Ein EE wird als DLL richten, sodass er, in der Debug-Engine (DE)-Adressraum oder des Visual Studio-Adressraums eingefügt wird, je nachdem, welche Entität die EE instanziiert.  
  
## <a name="managed-code-expression-evaluator"></a>Ausdrucksauswertung für verwalteten code  
 EE wird als eine Klassenbibliothek, eine DLL handelt, der sich mit der COM-Umgebung, die Schritte in der Regel durch einen Aufruf der VSIP-Programm registriert implementiert mit verwaltetem Code *regpkg.exe*. Der tatsächliche Prozess des Schreibens von die Registrierungsschlüssel für die COM-Umgebung wird automatisch durchgeführt.  
  
 Eine Methode "main"-Klasse ist mit markiert <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, der angibt, die die Methode aufgerufen werden, wenn die DLL mit COM registriert wird Diese Registrierungsmethode, die häufig aufgerufen `RegisterClass`, führt die Aufgabe der Registrierung der DLL mit Visual Studio. Eine entsprechende `UnregisterClass` (mit markiert die <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), macht die Auswirkungen der `RegisterClass` Wenn die DLL wird deinstalliert.  
 Die gleichen Registrierungseinträge erfolgen wie bei einer EE in nicht verwaltetem Code geschrieben werden; der einzige Unterschied ist, dass es keine Hilfsfunktion wie z. B. `SetEEMetric` für die Arbeit für Sie. Es folgt ein Beispiel für die Registrierung und Aufhebung der Registrierung zu.  
  
### <a name="example"></a>Beispiel  
 Die folgende Funktion zeigt, wie eine EE für verwaltete Code registriert, und selbst mit Visual Studio hebt die Registrierung.  
  
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
  
## <a name="unmanaged-code-expression-evaluator"></a>Ausdrucksauswertung von nicht verwaltetem code  
 Die EE-DLL implementiert die `DllRegisterServer` Funktion, um sich mit COM-Umgebung als auch Visual Studio zu registrieren.  
  
> [!NOTE]
>  Sie finden die MyCEE Registrierung Codebeispiel wird in der Datei *dllentry.cpp*, befindet sich in der VSIP-Installation unter EnVSDK\MyCPkgs\MyCEE.  
  
### <a name="dll-server-process"></a>DLL-Server-Prozess  
 Wenn Sie die EE, die DLL-Server zu registrieren:  
  
1.  Registriert die Klassenfactory `CLSID` gemäß den normalen COM-Konventionen.  
  
2.  Ruft die Hilfsfunktion `SetEEMetric` mit Visual Studio die EE-Metriken, die in der folgenden Tabelle gezeigt registrieren. Die Funktion `SetEEMetric` und die Metriken, die wie folgt angegeben werden, sind Teil der *dbgmetric.lib* Bibliothek. Finden Sie unter [SDK-Hilfsprogramme für das debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Details.  
  
    |Metrik|Beschreibung|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` der Factory EE-Klasse|  
    |`metricName`|Name des der EE als eine anzeigbare Zeichenfolge|  
    |`metricLanguage`|Der Namen der Sprache, die die EE ausgewertet werden soll|  
    |`metricEngine`|`GUID`s von der Debug-Engines (DE), die mit diesem EE arbeiten|  
  
    > [!NOTE]
    >  Die `metricLanguage``GUID` identifiziert die Sprache von Namen, aber es ist die `guidLang` Argument `SetEEMetric` , bei dem die Sprache ausgewählt. Wenn der Compiler die Debuginformationsdatei generiert, sollten die entsprechenden schreiben `guidLang` , damit die DE weiß, welche EE verwenden. Die DE fordert den symbolanbieter in der Regel für diese Sprache `GUID`, die in der Debug-Informationsdatei gespeichert ist.  
  
3.  Registriert bei Visual Studio erstellen, die Schlüssel unter HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, wobei *X.Y* ist die Version von Visual Studio zu registrieren.  
  
### <a name="example"></a>Beispiel  
 Die folgende Funktion zeigt, wie eine nicht verwaltete Code (C++) EE registriert, und selbst mit Visual Studio hebt die Registrierung.  
  
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
 [Schreiben Sie eine CLR-ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
