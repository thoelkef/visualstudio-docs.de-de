---
title: Registrieren eines Ausdrucksevaluators | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713192"
---
# <a name="register-an-expression-evaluator"></a>Registrieren eines Ausdrucksevaluators
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Der Ausdrucksauswertungswert (EE) muss sich als Klassenfactory sowohl in der Windows COM-Umgebung als auch in Visual Studio registrieren. Ein EE wird als DLL eingerichtet, sodass er entweder in den Adressraum des Debugmoduls (DE) oder in den Visual Studio-Adressraum eingefügt wird, je nachdem, welche Entität den EE instanziiert.

## <a name="managed-code-expression-evaluator"></a>Auswertung des Verwalteten Codeausdrucks
 Ein verwalteter Code EE wird als Klassenbibliothek implementiert, eine DLL, die sich selbst bei der COM-Umgebung registriert und in der Regel durch einen Aufruf des VSIP-Programms *regpkg.exe*gestartet wird. Der eigentliche Vorgang zum Schreiben der Registrierungsschlüssel für die COM-Umgebung wird automatisch behandelt.

 Eine Methode der Hauptklasse <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>ist mit gekennzeichnet, was darauf hinweist, dass die Methode aufgerufen werden soll, wenn die DLL bei COM registriert wird. Diese Registrierungsmethode, `RegisterClass`die häufig aufgerufen wird, führt die Aufgabe aus, die DLL bei Visual Studio zu registrieren. Ein `UnregisterClass` entsprechendes (mit der <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>gekennzeichnet) `RegisterClass` macht die Auswirkungen des Deinstallierten der DLL auf.
Die gleichen Registrierungseinträge werden wie bei einem EE erstellt, das in nicht verwaltetem Code geschrieben wurde. der einzige Unterschied ist, dass es `SetEEMetric` keine Helferfunktion gibt, die die Arbeit für Sie erledigen kann. Im Folgenden finden Sie ein Beispiel für den Registrierungs- und Entregistrierungsprozess.

### <a name="example"></a>Beispiel
 Die folgende Funktion zeigt, wie ein verwalteter Code EE registriert und sich selbst bei Visual Studio aufmacht.

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

## <a name="unmanaged-code-expression-evaluator"></a>Auswertung des nicht verwalteten Codeausdrucks
 Die EE-DLL `DllRegisterServer` implementiert die Funktion, sich selbst bei der COM-Umgebung und Visual Studio zu registrieren.

> [!NOTE]
> Sie finden den MyCEE-Code-Beispiel-Registrierungscode in der Datei *dllentry.cpp*, die sich in der VSIP-Installation unter EnVSDK-MyCPkgs-MyCEE befindet.

### <a name="dll-server-process"></a>DLL-Serverprozess
 Bei der Registrierung des EE der DLL-Server:

1. Registriert seine Klassenfactory `CLSID` gemäß normalen COM-Konventionen.

2. Ruft die Hilfsfunktion `SetEEMetric` auf, um die in der folgenden Tabelle gezeigten EE-Metriken bei Visual Studio zu registrieren. Die `SetEEMetric` Funktion und die folgenden Metriken sind Teil der *Bibliothek dbgmetric.lib.* Weitere Informationen finden Sie unter [SDK-Hilfsprogramme.](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

    |Metrik|BESCHREIBUNG|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`der EE-Klasse Fabrik|
    |`metricName`|Name des EE als anzeigebare Zeichenfolge|
    |`metricLanguage`|Der Name der Sprache, die die EE auswerten soll|
    |`metricEngine`|`GUID`s der Debug-Engines (DE), die mit diesem EE arbeiten|

    > [!NOTE]
    > Der `metricLanguage``GUID` identifiziert die Sprache anhand des `guidLang` Namens, aber es ist das `SetEEMetric` Argument, das die Sprache auswählt. Wenn der Compiler die Debug-Informationsdatei generiert, sollte er das entsprechende `guidLang` schreiben, damit die DE weiß, welche EE verwendet werden soll. Die DE fragt in der `GUID`Regel den Symbolanbieter nach dieser Sprache , die in der Debuginformationsdatei gespeichert ist.

3. Registriert sich bei Visual Studio, indem Sie Schlüssel\\unter HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio*X.Y*erstellen, wobei *X.Y* die Version von Visual Studio ist, bei der sie sich registrieren können.

### <a name="example"></a>Beispiel
 Die folgende Funktion zeigt, wie ein nicht verwalteter Code (C++) EE sich bei Visual Studio registriert und aufheben kann.

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

## <a name="see-also"></a>Weitere Informationen
- [Schreiben eines CLR-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [SDK-Hilfsprogramme zum Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
