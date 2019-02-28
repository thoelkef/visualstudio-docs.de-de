---
title: 'Exemplarische Vorgehensweise: Programmgesteuertes Erfassen von Grafikinformationen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fa8d750049d7d74d912e68544c91d5006252068
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722914"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Exemplarische Vorgehensweise: Programmgesteuertes Erfassen von Grafikinformationen
Sie können die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Grafikdiagnose zur programmgesteuerten Erfassung von Grafikinformationen aus einer Direct3D-App verwenden.

Programmgesteuerte Erfassung ist in Szenarien wie den folgenden nützlich:

- Beginnen Sie programmgesteuerte Erfassung, wenn Ihre Grafik-App kein vorhandenes Swapchain verwendet, etwa wenn sie auf einer Textur rendert.

- Beginnen Sie programmgesteuerte Erfassung, wenn Ihre Grafik-App überhaupt kein Rendern ausführt, etwa wenn in ihr DirectCompute verwendet wird, um Berechnungen auszuführen.

- Rufen Sie `CaptureCurrentFrame`auf, wenn ein Renderingproblem schwer durch manuelles Testen zu antizipieren und zu erfassen ist, aber programmgesteuert mithilfe von Informationen über den Status der App zur Laufzeit vorhergesagt werden kann.

## <a name="CaptureDX11_2"></a> Programmgesteuerte Erfassung in Windows 10
In diesem Teil der exemplarischen Vorgehensweise wird die programmgesteuerte Erfassung in Apps gezeigt, die die DirectX 11.2-API unter Windows 10 verwenden, in der die Methode der stabilen Erfassung verwendet wird.

In diesem Abschnitt wird gezeigt, wie folgende Aufgaben ausgeführt werden:

- Vorbereiten Ihrer App für die Verwendung der programmgesteuerten Erfassung

- Abrufen der Schnittstelle IDXGraphicsAnalysis

- Aufzeichnen von Grafikinformationen

> [!NOTE]
> Frühere Implementierungen der programmgesteuerten Erfassung basieren auf Remotetools für Visual Studio für [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um erfassungsfunktionalität bereitzustellen.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>Vorbereiten Ihrer App für die Verwendung der programmgesteuerten Erfassung
Um programmgesteuerte Erfassung in Ihrer App verwenden zu können, muss diese die erforderlichen Header enthalten. Diese Header sind Bestandteile des Windows 10 SDK.

##### <a name="to-include-programmatic-capture-headers"></a>So schließen Sie die Header für die programmgesteuerte Erfassung ein

- Schließen Sie diese Header in die Quelldatei ein, in der Sie die IDXGraphicsAnalysis-Schnittstelle definieren:

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > Schließen Sie nicht die Headerdatei „vsgcapture.h“ ein – diese unterstützt die programmgesteuerte Erfassung unter Windows 8.0 und früher –, um die programmgesteuerte Erfassung in Ihren Windows 10-Apps auszuführen. Dieser Header ist nicht mit DirectX 11.2 kompatibel. Wenn diese Datei enthalten ist, nachdem die d3d11_2.h-Header enthalten ist, gibt der Compiler eine Warnung aus. Wenn vor dem d3d11_2.h vsgcapture.h enthalten ist, wird die app nicht starten.

    > [!NOTE]
    > Wenn das DirectX SDK vom Juni 2010 auf Ihrem Computer installiert wurde und der Include-Pfad Ihres Projekts `%DXSDK_DIR%includex86`enthält, verschieben Sie diesen Teil an das Ende des Include-Pfads. Gehen Sie beim Bibliothekspfad genauso vor.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>Abrufen der Schnittstelle IDXGraphicsAnalysis
Bevor Sie Grafikinformationen von DirectX 11.2 erfassen können, müssen Sie die DXGI-Debugschnittstelle abrufen.

> [!IMPORTANT]
> Wenn Sie programmgesteuerte Erfassung verwenden zu können, müssen Sie weiterhin Ihre app unter der Grafikdiagnose ausführen (Alt + F5 in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) oder unter dem [Befehlszeilen-Erfassungs-Tool](command-line-capture-tool.md).

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>So rufen Sie die IDXGraphicsAnalysis-Schnittstelle ab

- Verwenden Sie den folgenden Code, um die IDXGraphicsAnalysis-Schnittstelle an die DXGI-Debugschnittstelle anzuschließen.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Sehen Sie sich die `HRESULT` zurückgegebenes [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) um sicherzustellen, dass Sie eine gültige Schnittstelle abrufen, bevor Sie sie verwenden:

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > Wenn `DXGIGetDebugInterface1` den Wert `E_NOINTERFACE` zurückgibt (`error: E_NOINTERFACE No such interface supported`), müssen Sie sicherstellen, dass die App unter der Grafikdiagnose (Alt+F5 in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).

### <a name="capturing-graphics-information"></a>Aufzeichnen von Grafikinformationen
Wenn Sie nun über eine gültige `IDXGraphicsAnalysis` -Schnittstelle verfügen, können Sie `BeginCapture` und `EndCapture` verwenden, um Grafikinformationen zu erfassen.

##### <a name="to-capture-graphics-information"></a>So erfassen Grafikinformationen

- Verwenden Sie `BeginCapture`, um mit der Erfassung von Grafikinformationen zu beginnen:

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    Die Erfassung beginnt sofort, wenn `BeginCapture` aufgerufen wird; es wird auf den nächsten Frame gewartet. Die Erfassung stoppt, wenn der aktuelle Frame dargestellt wird oder wenn Sie `EndCapture`aufrufen:

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- Nach dem Aufruf von `EndCapture`, das Graphics-Objekt frei.

## <a name="next-steps"></a>Nächste Schritte
In dieser exemplarische Vorgehensweise wurde veranschaulicht, wie Grafikinformationen programmatisch erfasst werden. Im nächsten Schritt haben Sie folgende Möglichkeit:

- Erfahren Sie, wie Sie erfasste Grafikinformationen mithilfe der Grafikdiagnose-Tools analysieren können. Finden Sie unter [Übersicht](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Erfassen von Grafikinformationen](walkthrough-capturing-graphics-information.md)
- [Capturing Graphics Information](capturing-graphics-information.md)
- [Befehlszeilen-Erfassungstool](command-line-capture-tool.md)
