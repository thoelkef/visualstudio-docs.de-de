---
title: 'Exemplarische Vorgehensweise: Aufzeichnen von Grafikinformationen programmgesteuert | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bbce760956dda7c9399d25dd241df26ec0e59644
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2018
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Exemplarische Vorgehensweise: Programmgesteuertes Erfassen von Grafikinformationen
Sie können die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Grafikdiagnose zur programmgesteuerten Erfassung von Grafikinformationen aus einer Direct3D-App verwenden.  
  
 Programmgesteuerte Erfassung ist in Szenarien wie den folgenden nützlich:  
  
-   Beginnen Sie programmgesteuerte Erfassung, wenn Ihre Grafik-App kein vorhandenes Swapchain verwendet, etwa wenn sie auf einer Textur rendert.  
  
-   Beginnen Sie programmgesteuerte Erfassung, wenn Ihre Grafik-App überhaupt kein Rendern ausführt, etwa wenn in ihr DirectCompute verwendet wird, um Berechnungen auszuführen.  
  
-   Rufen Sie `CaptureCurrentFrame`auf, wenn ein Renderingproblem schwer durch manuelles Testen zu antizipieren und zu erfassen ist, aber programmgesteuert mithilfe von Informationen über den Status der App zur Laufzeit vorhergesagt werden kann.  
  
##  <a name="CaptureDX11_2"></a>Programmgesteuerte Erfassung in Windows 10  
 In diesem Teil der exemplarischen Vorgehensweise wird die programmgesteuerte Erfassung in apps, die die DirectX 11.2-API unter Windows 10, verwenden Sie die Methode der stabilen Erfassung verwendet.
  
 In diesem Abschnitt wird gezeigt, wie folgende Aufgaben ausgeführt werden:  
  
-   Vorbereiten Ihrer App für die Verwendung der programmgesteuerten Erfassung  
  
-   Abrufen der Schnittstelle IDXGraphicsAnalysis  
  
-   Aufzeichnen von Grafikinformationen  
  
> [!NOTE]
>  Frühere Implementierungen der programmgesteuerten Erfassung basieren auf Remotetools für Visual Studio Tools for [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um erfassungsfunktionalität bereitzustellen.
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Vorbereiten Ihrer App für die Verwendung der programmgesteuerten Erfassung  
 Um programmgesteuerte Erfassung in Ihrer App verwenden zu können, muss diese die erforderlichen Header enthalten. Diese Header sind Teil des Windows 10-SDKS.  
  
##### <a name="to-include-programmatic-capture-headers"></a>So schließen Sie die Header für die programmgesteuerte Erfassung ein  
  
-   Schließen Sie diese Header in die Quelldatei ein, in der Sie die IDXGraphicsAnalysis-Schnittstelle definieren:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Schließen Sie nicht die Header-Datei vsgcapture.h—which unterstützt die programmgesteuerte Erfassung unter Windows 8.0 und früher –, die programmgesteuerte Erfassung in Ihren Windows 10-apps auszuführen. Dieser Header ist nicht mit DirectX 11.2 kompatibel. Wenn diese Datei enthalten ist, nachdem die d3d11_2.h-Header enthalten ist, gibt der Compiler eine Warnung aus. Wenn vor dem d3d11_2.h vsgcapture.h enthalten ist, wird die app nicht gestartet.  
  
    > [!NOTE]
    >  Wenn das DirectX SDK vom Juni 2010 auf Ihrem Computer installiert wurde und der Include-Pfad Ihres Projekts `%DXSDK_DIR%includex86`enthält, verschieben Sie diesen Teil an das Ende des Include-Pfads. Gehen Sie beim Bibliothekspfad genauso vor.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Abrufen der Schnittstelle IDXGraphicsAnalysis  
 Bevor Sie Grafikinformationen von DirectX 11.2 erfassen können, müssen Sie die DXGI-Debugschnittstelle abrufen.  
  
> [!IMPORTANT]
>  Wenn Sie programmgesteuerte Erfassung verwenden, müssen Sie weiterhin Ihre app unter der Grafikdiagnose ausführen (Alt + F5 in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) oder unter der [Befehlszeilen-Erfassungs-Tool](command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>So rufen Sie die IDXGraphicsAnalysis-Schnittstelle ab  
  
-   Verwenden Sie den folgenden Code, um die IDXGraphicsAnalysis-Schnittstelle an die DXGI-Debugschnittstelle anzuschließen.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Prüfen Sie unbedingt das von `HRESULT` zurückgegebene `DXGIGetDebugInterface1` , um sicherzugehen, dass Sie eine gültige Schnittstelle verwenden:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  Wenn `DXGIGetDebugInterface1` den Wert `E_NOINTERFACE` zurückgibt (`error: E_NOINTERFACE No such interface supported`), müssen Sie sicherstellen, dass die App unter der Grafikdiagnose (Alt+F5 in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
### <a name="capturing-graphics-information"></a>Aufzeichnen von Grafikinformationen  
 Wenn Sie nun über eine gültige `IDXGraphicsAnalysis` -Schnittstelle verfügen, können Sie `BeginCapture` und `EndCapture` verwenden, um Grafikinformationen zu erfassen.  
  
##### <a name="to-capture-graphics-information"></a>So erfassen Grafikinformationen  
  
- Verwenden Sie `BeginCapture`, um mit der Erfassung von Grafikinformationen zu beginnen:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Die Erfassung beginnt sofort, wenn `BeginCapture` aufgerufen wird; es wird auf den nächsten Frame gewartet. Die Erfassung stoppt, wenn der aktuelle Frame dargestellt wird oder wenn Sie `EndCapture`aufrufen:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  

- Nach dem Aufruf von `EndCapture`, Freigeben von Graphics-Objekts. 
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarische Vorgehensweise wurde veranschaulicht, wie Grafikinformationen programmatisch erfasst werden. Im nächsten Schritt haben Sie folgende Möglichkeit:  
  
-   Erfahren Sie, wie Sie erfasste Grafikinformationen mithilfe der Grafikdiagnose-Tools analysieren können. Finden Sie unter [Übersicht](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Aufzeichnen von Grafikinformationen](walkthrough-capturing-graphics-information.md)   
 [Aufzeichnen von Grafikinformationen](capturing-graphics-information.md)   
 [Befehlszeilen-Erfassungstool](command-line-capture-tool.md)