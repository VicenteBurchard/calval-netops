### Readme for processing of individual tiles of Sequoia sensor ### 

Images were processed for both tiles at the start (09:42 UTC) and end (09:50 UTC) of flight

1. Open-source methods 

1.1 The digital numbers (DN) 
---> corrected for lens distortion and fisheye lens.
---> based on script from: https://github.com/rasmusfenger/micasense_imageprocessing_sequoia
---> uploaded as 'Panels_DN_Sequoia_ICA_0942.tif'

1.2 Light corrected radiances  (Rad)
---> radiances were normalised based on sequoia sunshine sensor 
---> based on script from: https://github.com/rasmusfenger/micasense_imageprocessing_sequoia
---> equations available from SEQ AN 1 at https://forum.developer.parrot.com/t/parrot-announcement-release-of-application-notes/5455 
	 and also https://onedrive.live.com/?authkey=%21ACzNLk1ORe37aRQ&id=C34147D823D8DFEF%2115414&cid=C34147D823D8DFEF&parId=root&parQt=sharedby&parCid=88BB25612BECB065&o=OneUp 
---> uploaded as 'Panels_Rad_Sequoia_ICA_0942.tif'

1.3 Estimated 'reflectance' (Ref)	 
---> reflectance was estimated using the OpenDroneMap routines
---> based on https://github.com/OpenDroneMap/ODM/blob/master/opendm/multispectral.py 
---> uploaded as 'Panels_Ref_Sequoia_ICA_0942.tif'


2. Agisoft Metashape

files uploaded as: 'Panels_Ref_Sequoia_ICA_0942_Agisoft.tif' and 'Panels_Ref_Sequoia_ICA_0950_Agisoft.tif'

* No se emplea panel de calibración

2.1 Abrimos Agisoft Metashape y creamos proyecto.

2.2 Cargamos las imágenes de todo el dataset y seleccionamos multi-camera system

2.3 Calibramos la reflectancia de las capturas individuales utilizando el sensor de luz (DLS) 
en Tools/Calibrate Reflectance (en Parameters solo seleccionamos Use sun sensor).

2.4 Alineamos las capturas a partir de las posiciones geográficas y del solapamiento entre capturas. 
No es necesario añadir GCPs. 

2.5 Construimos la nube de puntos y la malla 3D.

2.6 Generamos el Modelo Digital de Elevaciones.

2.7 Generamos el ortomosaico.

2.8 Es necesario escalar los valores de reflectancia para ello abrimos la calculadora (Tools/Set Raster Transform) 
y normalizamos cada banda del sensor multiespectral dividiendo entre 32768.

2.9 Hasta aquí, los pasos a seguir son los mismos que para generar el ortomosaico fotogramétrico, con la
diferencia de que en lugar de exportar el ortomosaico, se selecciona el tile individual que nos interesa
(en este caso, el de la zona de paneles), y le damos a exportar orthophoto en la ventana que se abre 
seleccionamos Selected cameras y en Raster transform hay que elegir Index value (no Index color!), 
de forma que se exportará una captura individual con las reflectancias calibradas. 

