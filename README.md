# build-pip-package
Easy guide on how to make a python package of your own and then uploading it on pypi.org so that it can be installed using pip. 

Prerequisites:
1. You should have an account on pypi.org
2. You should have the lastest version of python(save the python folder in C Drive).
3. You should have pip installed.

Instructions:
1. Make a folder(this will contain the file(s) that you want to upload on PyPI)
2. Add the follwing files in that folder:
   a) program.py (the main code)
   b) README.md (include information about the project)
   c) setup.py (add the following lines in the file):
      import setuptools
      with open("README.md", "r") as fh:
        long_description = fh.read()
      setuptools.setup
      (
        name='dokr',  
        version='0.1',
        scripts=['dokr'] ,
        author="Deepak Kumar",
        author_email="deepak.kumar.iet@gmail.com",
        description="A Docker and AWS utility package",
        long_description=long_description,
        long_description_content_type="text/markdown",
        url="https://github.com/javatechy/dokr",
        packages=setuptools.find_packages(),
        classifiers=[
          "Programming Language :: Python :: 3",
          "License :: OSI Approved :: MIT License",
          "Operating System :: OS Independent",
        ],
      )
   d) LICENSE (if required):
      eg.
      Copyright (c) 2019 The Python Packaging Authority

      Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files         (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify,             merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is               furnished to do so, subject to the following conditions:

      The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

      THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF       MERCHANTABILITY,FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE       FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,OUT OF OR CONNECTION       WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
   e) .pypirc:
      [distutils] 
      index-servers=pypi
      [pypi] 
      repository = https://upload.pypi.org/legacy/ 
      username =[your PyPI username]
3. A few packages are required- setup, wheel, twine, tqdm. Type these lines on your command prompt(to check if they are already there and if not then to install the respective latest versions):
   pip install --upgrade pip setuptools wheel
   pip install tqdm
   pip install --user --upgrade twine
4. Open the folder you made press Alt+D to go to the address bar then type "cmd", press enter and then in the prompt 
   type "python -m twine upload dist/*".
5. Enter your PyPI password when asked for it.

There you go, now you have successfully uploaded your code/project on PyPI and it can be installed on any device using the pip install command on command prompt.
