---
title: HRESULT-Informationen in verwaltetem Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: douge
ms.openlocfilehash: c87fc618f1c80b60bbd2f95537dc70a83eb2bdc7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509573"
---
# <a name="hresult-information-in-managed-code"></a>HRESULT-Informationen in verwaltetem Code
Die Interaktion zwischen verwaltetem Code und COM kann Probleme verursachen, wenn HRESULT-Rückgabewerte gefunden werden.  
  
 In einer COM-Schnittstelle kann ein HRESULT-Rückgabewert die folgenden Rollen erfüllen:  
  
-   Bereitstellen von Fehlerinformationen (z. B. <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>).  
  
-   Bereitstellen von Statusinformationen zum normalen Programmverhalten  
  
 Wenn COM Aufrufe in verwaltetem Code ausführt, können HRESULTs die folgenden Probleme verursachen:  
  
-   COM-Funktionen, die HRESULT-Werte kleiner als 0 (Fehlercodes) zurückgeben, generieren Ausnahmen.  
  
-   COM-Methoden, die regelmäßig zwei oder mehr unterschiedliche Erfolgscodes, z. B. zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK> oder <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, können nicht unterschieden werden.  
  
 Da viele der [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] COM-Funktionen entweder HRESULT-Werte kleiner als 0 (null) oder unterschiedliche Erfolgscodes Zurückgeben der [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] interop-Assemblys wurden geschrieben, damit die Methodensignaturen beibehalten werden. Alle [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Interop-Methoden sind vom `int` Typ. HRESULT-Werte werden über die Interop-Schicht ohne Veränderung und ohne Generierung von Ausnahmen übergeben.  
  
 Da eine COM-Funktion ein HRESULT an die sie aufrufende verwaltete Methode zurückgibt, muss die aufrufende Methode das HRESULT überprüfen und ggf. Ausnahmen auslösen.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Behandeln von HRESULTs, die von COM an verwalteten Code zurückgegeben werden  
 Wenn Sie eine COM-Schnittstelle in verwaltetem Code aufrufen, überprüfen Sie den HRESULT-Wert, und lösen Sie ggf. eine Ausnahme aus. Die <xref:Microsoft.VisualStudio.ErrorHandler> -Klasse enthält die <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> übergebenen Methode, die abhängig vom Wert von HRESULT eine COM-Ausnahme auslöst.  
  
 In der Standardeinstellung <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> löst eine Ausnahme aus, wenn sie ein HRESULT übergeben wird, die einen Wert kleiner als 0 (null) ist. In Fällen, in denen solche HRESULTs zulässige Werte sind und keine Ausnahme ausgelöst werden soll, die Werte der zusätzlichen HRESULTS an übergeben werden sollte <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> nach die Werten getestet werden. Wenn das zu testende HRESULT alle HRESULT-Werte, die explizit übergeben entspricht <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, wird keine Ausnahme ausgelöst.  
  
> [!NOTE]
>  Die <xref:Microsoft.VisualStudio.VSConstants> -Klasse enthält Konstanten für allgemeine HRESULTS, z. B. <xref:Microsoft.VisualStudio.VSConstants.S_OK> und <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, und [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HRESULTs vorzusehen, z. B. <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> und <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> bietet außerdem die <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> und <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> Methoden, die den Makros SUCCEEDED und FAILED in COM entsprechen  
  
 Betrachten Sie beispielsweise den folgenden Funktionsaufruf, in dem <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> ist ein zulässiger Rückgabewert aber alle anderen HRESULTs kleiner als 0 (null) stellt einen Fehler dar.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Wenn es mehrere zulässige Rückgabewerte gibt, zusätzliche HRESULT-Werte können nur angefügt werden der Liste auf den Aufruf von <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Von verwaltetem Code an COM zurückgegebene HRESULTS  
 Wenn keine Ausnahme auftritt, gibt der verwaltete Code <xref:Microsoft.VisualStudio.VSConstants.S_OK> der COM-Funktion, die diese aufgerufen. COM-Interop unterstützt allgemeine Ausnahmen, die in verwaltetem Code stark typisiert sind. Zum Beispiel eine Methode, die ein unzulässiges empfängt `null` Argument löst eine <xref:System.ArgumentNullException>.  
  
 Wenn Sie nicht sicher sind welche Ausnahme ausgelöst, aber Sie wissen, dass das HRESULT zurückgegeben werden soll, COM, können Sie die <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Methode, um eine entsprechende Ausnahme auszulösen. Dies funktioniert auch bei einem nicht standardmäßigen Fehler, z. B. <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> versucht, den HRESULT-Wert zugeordnet, die in eine stark typisierte Ausnahme an es übergeben werden. Wenn dies nicht möglich ist, wird stattdessen eine generische COM-Ausnahme ausgelöst. Das endgültige Ergebnis ist, dass das HRESULT an Sie übergeben <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> aus verwaltetem Code wird zurückgegeben, um die COM-Funktion, die diese aufgerufen.  
  
> [!NOTE]
>  Ausnahmen beeinträchtigen die Leistung und dienen als Hinweis auf anormale Programmbedingungen. Häufig auftretende Bedingungen sollten inline behandelt werden, statt eine Ausnahme auszulösen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltete VSPackages](../misc/managed-vspackages.md)   
 [Interoperation mit nicht verwaltetem Code](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Vorgehensweise: Zuordnen von HRESULTs und Ausnahmen](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Erstellen von COM-Komponenten für die Interoperation](http://msdn.microsoft.com/en-us/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Verwaltete VSPackages](../misc/managed-vspackages.md)