---
title: Verwenden einer requirements.txt-Datei zum Verwalten von Paketanforderungen | Microsoft-Dokumentation
description: "Sie können eine requirements.txt-Datei verwenden, um die Abhängigkeiten eines Projekts zu verwalten. Wenn Sie ein Projekt erhalten, das eine requirements.txt-Datei enthält, können Sie diese Abhängigkeiten ganz einfach in nur einem Schritt installieren."
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 808e7a66d4e0130ee8080b124b33b22561bb2a58
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2018
---
# <a name="managing-required-packages-with-requirementstxt"></a>Verwalten von erforderlichen Paketen mit „requirements.txt“

Wenn Sie ein Projekt über ein Buildsystem für andere Benutzer freigeben oder planen, um es [in Microsoft Azure zu veröffentlichen](python-azure-cloud-service-project-template.md), müssen Sie die externen Pakete angeben, die das Projekt benötigt. Der empfohlene Ansatz ist die Verwendung einer [requirements.txt-Datei](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org), die eine Liste der Befehle für pip enthält, mit denen die erforderlichen Versionen der abhängigen Pakete installiert werden.

Eigentlich kann jeder Dateiname zum Nachverfolgen von Anforderungen verwendet werden (mit `-r <full path to file>` beim Installieren eines Pakets), aber Visual Studio bietet spezielle Unterstützung für `requirements.txt`:

- Wenn Sie ein Projekt geladen haben, das `requirements.txt` enthält, und alle in der Datei aufgeführten Pakete installieren möchten, erweitern Sie den Knoten **Python-Umgebungen** im **Projektmappen-Explorer**, klicken Sie dann mit der rechten Maustaste auf den Umgebungsknoten, und wählen Sie **Aus „requirements.txt“ installieren** aus:

    ![Installieren aus „requirements.txt“](media/environments-requirements-txt-install.png)

- Wenn Sie alle erforderlichen Pakete bereits in einer Umgebung installiert haben, können Sie im Projektmappen-Explorer mit der rechten Maustaste auf diese Umgebung klicken und **„requirements.txt“ generieren** auswählen, um die erforderliche Datei zu erstellen. Wenn die Datei bereits vorhanden ist, werden Sie zum Aktualisieren der Datei aufgefordert:

    ![Optionen für die Aktualisierung von „requirements.txt“](media/environments-requirements-txt-replace.png)

  - **Gesamte Datei ersetzen** entfernt alle vorhandenen Elemente, Kommentare und Optionen.
  - **Vorhandene Einträge aktualisieren** erkennt Paketanforderungen und aktualisiert die Versionsbezeichner entsprechend der derzeit installierten Version.
  - **Aktualisieren und Einträge hinzufügen** aktualisiert alle gefundenen Anforderungen und fügt alle anderen Pakete am Ende der Datei hinzu.

Da mit `requirements.txt`-Dateien die Anforderungen einer Umgebung fixiert werden sollen, werden alle installierten Pakete mit genauen Versionen aufgeführt. Wenn Sie genaue Versionen verwenden, wird sichergestellt, dass Sie Ihre Umgebung leicht auf einem anderen Computer reproduzieren können. Pakete werden aufgenommen, selbst wenn sie mit einem Versionsbereich, als Abhängigkeit von einem anderen Paket oder mit einen anderen Installationsprogramm als pip installiert wurden.

Wenn ein Paket nicht von pip installiert werden kann und in einer `requirements.txt`-Datei enthalten ist, schlägt die gesamte Installation fehl. Bearbeiten Sie in diesem Fall die Datei manuell, um dieses Paket ausschließen oder [pip-Optionen](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) zu verwenden, um auf eine installierbare Version des Pakets zu verweisen. Sie könnten beispielsweise [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) verwenden, um eine Abhängigkeit zu kompilieren und die Option `--find-links <path>` Ihrer Datei `requirements.txt` hinzuzufügen:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>Siehe auch

- [Verwalten von Python-Umgebungen in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Auswählen eines Interpreters für ein Projekt](selecting-a-python-environment-for-a-project.md)
- [Suchpfade](search-paths.md)
- [Das Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md)