# Octave
Octave scripting OpenModelica interface using ZEROMQ

# Requirement:
[Openmodelica](https://www.openmodelica.org/)<br>
[Octave](https://octave.org/)<br>
[zeromq](https://zeromq.org/)<br>

# Installation
Clone the repository and add the installation directory to Octave PATH for future sessions. For Example <br>

```
installing zeromq
>>> pkg install -forge zeromq
```

```
from the Octave terminal, edit or create config file

The config file should be created in home directory, the below command will show the home directory
>>> prefdir
ans: "C:\Users\arupa54"
>>> cd ("C:/Users/arupa54)
>>> edit .octaverc
The above command will open the config file in Octave editor, now add the following commands to the ".octaverc" file

addpath("C:/OPENMODELICAGIT/OpenModelica/OMOctave");
javaaddpath ("C:/OPENMODELICAGIT/OpenModelica/OMOctave/xercesImpl.jar");
javaaddpath ("C:/OPENMODELICAGIT/OpenModelica/OMOctave/xml-apis.jar");

The xml parser uses the xerces java library and two jar files are needed "xercesImpl.jar" and "xml-apis.jar" which is provided in the repository, you can also
download the jar files in the following link https://xerces.apache.org/mirrors.cgi#binary

You can also directly use the OMOctave package directly from the directory where you have cloned, without need to perform the above steps. But the package cannot be used globally.
```


```

# Usage
```
>>> omc=OMOctave();
>>> omc.sendExpression("getVersion()")
"v1.13.0-dev-531-gde26b558a (64-bit)"
>>> omc.sendExpression("model a end a;")
"{a}"
>>> omc.sendExpression('loadFile("C:\OMMatlab\BouncingBall.mo")')
true
>>> omc.sendExpression("getClassNames()")
{a,BouncingBall}
>>> omc.sendExpression("simulate(BouncingBall)")
record SimulationResult
    resultFile = "C:/Users/arupa54/BouncingBall_res.mat",
    simulationOptions = "startTime = 0.0, stopTime = 1.0, numberOfIntervals = 500, tolerance = 1e-006, method = 'dassl', fileNamePrefix = 'BouncingBall', options = '', outputFormat = 'mat', variableFilter = '.*', cflags = '', simflags = ''",
    messages = "LOG_SUCCESS       | info    | The initialization finished successfully without homotopy method.
LOG_SUCCESS       | info    | The simulation finished successfully.
",
    timeFrontend = 0.03334629789025638,
    timeBackend = 0.05818852816547053,
    timeSimCode = 0.02908068832276598,
    timeTemplates = 0.04130980342652182,
    timeCompile = 4.495768417986718,
    timeSimulation = 0.135430370984969,
    timeTotal = 4.795528603068404
end SimulationResult;
```
To see the list of available OpenModelicaScripting API see    (https://www.openmodelica.org/doc/OpenModelicaUsersGuide/latest/scripting_api.html
