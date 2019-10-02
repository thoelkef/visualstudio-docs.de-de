---
title: Ausführen von Komponententests für containerisierte Apps
author: ghogen
description: Ausführen von Komponententests für jeden Build eines Docker-Projekts in Visual Studio
ms.author: ghogen
ms.date: 06/17/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: ec5aea44362cf82f6745671cc0706f80e01a60ad
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2019
ms.locfileid: "71125968"
---
# <a name="how-to-run-unit-tests-for-a-containerized-app"></a>Gewusst wie: Ausführen von Komponententests für containerisierte Apps

Sie können Komponententests für jeden Build eines containerisierten Projekts ausführen, indem Sie Ihre Dockerfile-Datei ändern.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)
- Komponententests, die für die Verwendung von [dotnet test](/dotnet/core/tools/dotnet-test) eingerichtet sind
- [Fenstererweiterung „Container“](https://aka.ms/vscontainerspreview)

## <a name="add-unit-tests-to-the-dockerfile"></a>Hinzufügen von Komponententests zur Dockerfile-Datei

Visual Studio führt vor dem Ändern der Dockerfile-Datei einige besondere Leistungsoptimierungen durch. Beim Erstellen der **Debugkonfiguration** erstellt Visual Studio Projekte auf dem lokalen Computer und kopiert die Ergebnisse in den Container. Es wird also nur die erste Stufe der mehrstufigen Dockerfile-Datei so ausgeführt, wie in der Dockerfile-Datei angegeben. Weitere Informationen finden Sie unter [Buildprozess für Containertools für Visual Studio](container-build.md).

Fügen Sie der Dockerfile-Datei zwischen den Stufen `build` und `publish` eine `unit-test`-Stufe hinzu, um einer mehrstufigen Dockerfile-Datei Komponententests hinzuzufügen.

```
FROM build AS unit-test
RUN dotnet unit-test --logger:trx
```

Visual Studio führt in der **Debugkonfiguration** nur die erste Stufe aus, sodass die Stufe `unit-test` nur in der **Releasekonfiguration** ausgeführt wird. Doch auch in der **Releasekonfiguration** sind die Protokollergebnisse nicht im endgültigen Image enthalten, das aus der `base`-Stufe erstellt wird, nicht aus der Stufe `unit-test`. Verwenden Sie den folgenden Befehl, um die Tests auszuführen und ein Image zu erstellen, in dem die Protokolle angezeigt werden:

```cmd
docker build --target:unit-test
```

## <a name="next-steps"></a>Nächste Schritte

Sie können das Fenster [Container](view-and-diagnose-containers.md) verwenden (sofern die entsprechende Erweiterung installiert ist), um die Testprotokolle anzuzeigen.  

Drücken Sie zum Anzeigen der Testprotokolle auf **STRG**+**Q**, und suchen Sie nach **Container**, um das Fenster **Container** zu öffnen. Suchen Sie im Fenster **Container** Ihren Container, und öffnen Sie die Registerkarte **Dateien**. Suchen Sie im Dateisystem des Containers nach der Testergebnisdatei (TRX-Datei), und öffnen Sie sie, um die Ergebnisse in Visual Studio anzuzeigen.

