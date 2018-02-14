---
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Durchsuchen des Speichers, um Daten hochzuladen oder Modelle und Protokolle herunterzuladen

Sie können den gesamten Speicher auf dem Remotecomputer oder der Azure-Dateifreigabe durchsuchen, um das Hochladen von Daten oder das Herunterladen von Modellen und Protokollen zu ermöglichen. Oder wenn Sie auf Protokolle und Auftragsausgaben für einen bestimmten Auftrag zugreifen möchten, können Sie dies auch im Auftragsbrowser tun.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>So greifen Sie auf alle Daten auf dem Remotecomputer oder der Dateifreigabe zu
1. Öffnen Sie den **Server-Explorer**.
2. Erweitern Sie den Remotecomputer oder den Computekontext „Batch AI“.
3. Klicken Sie mit der rechten Maustaste auf **Speicher** und dann auf **Durchsuchen**.

    ![storage](media\manage-storage\browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>So greifen Sie auf auftragsspezifische Daten auf dem Remotecomputer oder der Dateifreigabe zu
1. Öffnen Sie den [Auftragsverlauf](job-details.md).
2. Wählen Sie den Auftrag aus.
3. Klicken Sie auf **Arbeitsordner** oder auf „StdOut/Stderr“, um schnell auf diese wichtigen Protokolldateien zuzugreifen. 

    ![storage](media\manage-storage\job-workingfolder.png)
