# WebAi
Details of WebAi SDK
--- Exploring package: webai_element_sdk ---

Help for the main package (webai_element_sdk):
Help on package webai_element_sdk:

NAME
    webai_element_sdk

PACKAGE CONTENTS
    __main__
    comms (package)
    element (package)
    runner (package)

CLASSES
    builtins.object
        webai_element_sdk.element.element.Element
    typing.Generic(builtins.object)
        webai_element_sdk.element.context.Context
    
    class Context(typing.Generic)
     |  Context(inputs: ~I, outputs: ~O, settings: ~S, logger: webai_element_sdk.comms.agent.AgentComms, preview_port: Optional[int] = None) -> None
     |  
     |  Element context data type
     |  
     |  Attributes:
     |      inputs (I): Element input context
     |      outputs (O): Element output context
     |      settings (S): Element settings context
     |      logger (AgentComms): The logging instance
     |      preview_port (Optional[int]): Network port for accessing element preview/visualization data (if any)
     |  
     |  Method resolution order:
     |      Context
     |      typing.Generic
     |      builtins.object
     |  
     |  Methods defined here:
     |  
     |  __eq__(self, other)
     |      Return self==value.
     |  
     |  __init__(self, inputs: ~I, outputs: ~O, settings: ~S, logger: webai_element_sdk.comms.agent.AgentComms, preview_port: Optional[int] = None) -> None
     |      Initialize self.  See help(type(self)) for accurate signature.
     |  
     |  __repr__(self)
     |      Return repr(self).
     |  
     |  ----------------------------------------------------------------------
     |  Data descriptors defined here:
     |  
     |  __dict__
     |      dictionary for instance variables (if defined)
     |  
     |  __weakref__
     |      list of weak references to the object (if defined)
     |  
     |  ----------------------------------------------------------------------
     |  Data and other attributes defined here:
     |  
     |  __annotations__ = {'inputs': ~I, 'logger': <class 'webai_element_sdk.c...
     |  
     |  __dataclass_fields__ = {'inputs': Field(name='inputs',type=~I,default=...
     |  
     |  __dataclass_params__ = _DataclassParams(init=True,repr=True,eq=True,or...
     |  
     |  __hash__ = None
     |  
     |  __match_args__ = ('inputs', 'outputs', 'settings', 'logger', 'preview_...
     |  
     |  __orig_bases__ = (typing.Generic[~I, ~O, ~S],)
     |  
     |  __parameters__ = (~I, ~O, ~S)
     |  
     |  preview_port = None
     |  
     |  ----------------------------------------------------------------------
     |  Class methods inherited from typing.Generic:
     |  
     |  __class_getitem__(params) from builtins.type
     |  
     |  __init_subclass__(*args, **kwargs) from builtins.type
     |      This method is called when a class is subclassed.
     |      
     |      The default implementation does nothing. It may be
     |      overridden to extend subclasses.
    
    class Element(builtins.object)
     |  Element(id: uuid.UUID, name: str, version: Optional[str] = None, display_name: Optional[str] = None, settings: Optional[webai_element_sdk.element.settings.ElementSettings] = None, inputs: Optional[webai_element_sdk.element.variables.ElementInputs] = None, outputs: Optional[webai_element_sdk.element.variables.ElementOutputs] = None, packages: Optional[List[str]] = [], is_training: Optional[bool] = False, is_inference: Optional[bool] = False, sub_elements: Optional[List[ForwardRef('Element')]] = [], parent_element_id: Optional[str] = '', training_metrics_schema: Optional[Dict[str, Any]] = None, metrics_schema: Optional[Dict[str, Any]] = None, element_progress_schema: Optional[Dict[str, float]] = None, description: Optional[str] = None, init_run: bool = False)
     |  
     |  Class used to instantiate an element
     |  
     |  Attributes:
     |      id (UUID): The element identifier
     |      name (str): The name of the element
     |      version (Optional[str]): The semantic version of the element
     |      display_name (Optional[str]): The name of the element to use for UI display purposes
     |      settings (Optional[ElementSettings]): The element settings attributed to the element
     |      inputs (Optional[ElementInputs]): The inputs to be operated upon by the element
     |      outputs (Optional[ElementOutputs]): The outputs provided by the element for downstream consumption
     |      packages (Optional[List[str]]): TODO
     |      is_training (Optional[bool]): Does this element perform traditional ML training functions?
     |      is_inference (Optional[bool]): Does this element perform traditional ML inference functions?
     |      sub_elements (Optional[List["Element"]]): TODO
     |      parent_element_id (Optional[str]): TODO
     |      description (Optional[str]): A short, user facing description of what the element does
     |      agent_comms (AgentComms): The runtime agent communication instance
     |      startup_func (Coroutine[Any, Any, None]): The function registered via decorator to be executed at element startup
     |      executor_func (Coroutine[Any, Any, None]): The function registered via decorator to be executed continuously as the element's main process
     |      shutdown_func (Coroutine[Any, Any, None]): The function registered via decorator to be executed at element shutdown or termination
     |      ctx (Context): The context object providing element detail/state at execution time
     |  
     |  Methods defined here:
     |  
     |  __init__(self, id: uuid.UUID, name: str, version: Optional[str] = None, display_name: Optional[str] = None, settings: Optional[webai_element_sdk.element.settings.ElementSettings] = None, inputs: Optional[webai_element_sdk.element.variables.ElementInputs] = None, outputs: Optional[webai_element_sdk.element.variables.ElementOutputs] = None, packages: Optional[List[str]] = [], is_training: Optional[bool] = False, is_inference: Optional[bool] = False, sub_elements: Optional[List[ForwardRef('Element')]] = [], parent_element_id: Optional[str] = '', training_metrics_schema: Optional[Dict[str, Any]] = None, metrics_schema: Optional[Dict[str, Any]] = None, element_progress_schema: Optional[Dict[str, float]] = None, description: Optional[str] = None, init_run: bool = False)
     |      Element constructor
     |      
     |      Args:
     |          id: The element identifier
     |          name: The name of the element
     |          version: The semantic version of the element
     |          display_name: The name of the element to use for UI display purposes
     |          settings: The element settings attributed to the element
     |          inputs: The inputs to be operated upon by the element
     |          outputs: The outputs provided by the element for downstream consumption
     |          init_run: Request initial run of @element.executor without input frames present
     |          packages: TODO
     |          is_training: Does this element perform traditional ML training functions?
     |          is_inference: Does this element perform traditional ML inference functions?
     |          sub_elements: TODO
     |          parent_element_id: TODO
     |          training_metrics_schema: Schema used to define charts for run history
     |          metrics_schema: Schema used to define charts for run history
     |          element_progress_schema: Schema used to define progress statuses
     |          description: A short, user facing description of what the element does
     |      
     |      Raises:
     |          BaseException: `name` argument cannot be empty
     |          BaseException: `version` argument must use semantic versioning
     |  
     |  executor(self, func: Optional[Callable[[webai_element_sdk.element.context.Context[webai_element_sdk.element.variables.ElementInputs | None, webai_element_sdk.element.variables.ElementOutputs | None, webai_element_sdk.element.settings.ElementSettings | None]], collections.abc.AsyncIterator[Any]]] = None)
     |      Decorator to be used to define ongoing element process execution
     |  
     |  generate_metadata(self)
     |  
     |  refresh(self, func: Callable[[webai_element_sdk.element.context.Context[webai_element_sdk.element.variables.ElementInputs | None, webai_element_sdk.element.variables.ElementOutputs | None, webai_element_sdk.element.settings.ElementSettings | None]], NoneType])
     |      Decorator to be used to define behavior that should execute when element settings are refreshed
     |  
     |  async run(self)
     |  
     |  shutdown(self, func: Callable[[Any], Coroutine[Any, Any, Any]])
     |      Decorator to be used to define behavior that should execute after general element process execution (i.e., at shutdown or termination of the process)
     |  
     |  startup(self, func: Callable[[Any], Coroutine[Any, Any, Any]])
     |      Decorator to be used to define behavior that should execute ahead of the general element process execution
     |  
     |  ----------------------------------------------------------------------
     |  Data descriptors defined here:
     |  
     |  __dict__
     |      dictionary for instance variables (if defined)
     |  
     |  __weakref__
     |      list of weak references to the object (if defined)

DATA
    __all__ = ['Element', 'Context']

FILE
    /Users/trevor.kennedy/code/elements/vis/display/venv/lib/python3.10/site-packages/webai_element_sdk/__init__.py



--- Submodules/Components found: ---

Component: __main__
  Is package: False
Usage: inspect_package.py [OPTIONS] COMMAND [ARGS]...

Options:
  --help  Show this message and exit.

Commands:
  generate
======
More Information
Element Boilerplate

The webai_element_sdk library exposes everything you need to create elements.
Decorators

@element.startup
async def startup(ctx: Context[Inputs, Outputs, None]):
    print(f"Starting...")

@element.shutdown
async def shutdown(ctx: Context[Inputs, Outputs, None]):
    print(f"Shutting down...")

@element.executor
async def run(ctx: Context[Inputs, Outputs, Settings]):
    print(f"Hello world...")
    # Main element logic goes here

Element Settings

Configurable UI parameters in Navigator to guide element behavior.

"""
Boolean Settings
Implemented as a toggle button
"""

boolean_setting = BoolSetting(
    name="boolean_setting",
    display_name="Boolean Setting",
    default=True
)

"""
Number Settings
Integer and Float
"""

# Integer displayed as input fields by default
integer_setting = NumberSetting[int](
    name="integer_setting",
    display_name="Integer Setting",
    default=256,
    min_value=0,
    max_value=1024,
    step=1,
)

# Providing "valid_values" creates a dropdown
dropdown_setting_with_int_values = NumberSetting[int](
    name="dropdown_setting_with_int_values",
    display_name="Int Dropdown Setting",
    valid_values=[0, 1, 2, 3, 4, 5],
    default=1,
)

# Float displayed as sliders by default
float_setting = NumberSetting[float](
    name="float_setting",
    display_name="Float Setting",
    default=0.1,
    min_value=0,
    max_value=1,
    step=0.01,
)

# Providing "valid_values" creates a dropdown
dropdown_setting_with_float_values = NumberSetting[float](
    name="dropdown_setting_with_float_values",
    display_name="Float Dropdown Setting",
    valid_values=[0.0, 0.1, 0.2, 0.3, 0.4, 0.5],
    default=0.1,
)

"""
Text Settings
Displayed as input fields by default
"""

text_setting = TextSetting(
    name="text_setting",
    display_name="Text Setting",
    default="Hello, World!",
)

# Providing "valid_values" creates a dropdown
dropdown_setting_with_text = TextSetting(
    name="dropdown_setting_with_text",
    display_name="Text Dropdown Setting",
    valid_values=["Option 1", "Option 2", "Option 3"],
    default="Option 2",
)

# "file_path" hint displays file path selector
file_path_setting = TextSetting(
    name="file_path_setting",
    display_name="File Path Setting",
    default="~/path/to/my/file.txt",
    hints=["file_path"]
)

# "folder_path" hint displays file path selector
folder_path_setting = TextSetting(
    name="folder_path_setting",
    display_name="Folder Path Setting",
    default="~/path/to/my/folder",
    hints=["folder_path"]
)
