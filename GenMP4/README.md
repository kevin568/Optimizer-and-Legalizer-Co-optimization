# Requirements
- **Platform**: Tested on Windows. Other platforms have not been tested.
- The environment can be set up using the `environment.yml` file.
- **PyOpenGL Issue**: Installing PyOpenGL directly with `pip` may not work. If you encounter issues, download and install the appropriate wheel file manually from [here](https://github.com/cgohlke/pyopengl-build/releases/tag/v3.1.8).

# Usage
To run the visualizer, use the following command:
```bash
$ main.py -lg *.lg -opt *.opt -postlg *_post.lg -o output.mp4
```
Alternatively, you can run the executable file:
```bash
$ visualizer.exe -lg *.lg -opt *.opt -postlg *_post.lg -o output.mp4
```
- The `.exe` file is packaged with `pyinstaller` using the command:
```
$ pyinstaller --onefile --name visualizer main.py
```
- The visualizer will generate a 60 FPS MP4 video, where each step is displayed for 1 frame (1/60 s).

# Result
- The results are based on the solution provided by my Legalizer and are intended for reference only.

|      Testcase     |# of Steps|# of Moved Cells|Output time|Runtime|Generate Speed|
|-------------------|----------|----------------|-----------|-------|--------------|
|  testcase1_16900  |    1781  |      1438      |    29s    | 44.45s|   40.07fps   |
|testcase1_ALL0_5000|    3420  |      8420      |    57s    | 87.23s|   39.21fps   |
|   testcase2_100   |    2949  |      654       |    49s    | 81.92s|   36.00fps   |
|testcase1_MBFF_LIB_7000|9632  |      9396      |    160s   |300.36s|   32.07fps   |

Here is an example video generated by the visualizer:

https://github.com/user-attachments/assets/88aff6f9-eb5d-4a24-b792-8ab3ea50d211

https://github.com/user-attachments/assets/4306608e-f9d9-4c46-9a3b-f2ad720b55c6

Since the videos of other test cases are too large to upload to the GitHub README, only the smallest test case (`testcase1_16900`) is shown here. For other test cases, refer to the MP4 files in the folder.
> [!NOTE]
> Since the generated videos can be large, the above demo video has been compressed using `ffmpeg`. To compress your own videos, use the following command:
> ```
> $ ffmpeg -i "{filename}.mp4" -c:v libx264 -crf 18 -preset veryfast -c:a copy "{filename}_compress.mp4
> ```
> - The larger the CRF value, the smaller the bitrate, but also the lower the video quality.
