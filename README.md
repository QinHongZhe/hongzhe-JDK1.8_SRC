# JDK 1.8 源码阅读 (心得笔记)

# 目录结构

    

```
├─com   // SUN 官方
│  └─sun
│      ├─corba
│      │  └─se
│      │      ├─impl
│      │      │  ├─activation
│      │      │  ├─copyobject
│      │      │  ├─corba
│      │      │  ├─dynamicany
│      │      │  ├─encoding
│      │      │  ├─interceptors
│      │      │  ├─io
│      │      │  ├─ior
│      │      │  │  └─iiop
│      │      │  ├─javax
│      │      │  │  └─rmi
│      │      │  │      └─CORBA
│      │      │  ├─legacy
│      │      │  │  └─connection
│      │      │  ├─logging
│      │      │  ├─monitoring
│      │      │  ├─naming
│      │      │  │  ├─cosnaming
│      │      │  │  ├─namingutil
│      │      │  │  └─pcosnaming
│      │      │  ├─oa
│      │      │  │  ├─poa
│      │      │  │  └─toa
│      │      │  ├─orb
│      │      │  ├─orbutil
│      │      │  │  ├─closure
│      │      │  │  ├─concurrent
│      │      │  │  ├─fsm
│      │      │  │  ├─graph
│      │      │  │  └─threadpool
│      │      │  ├─presentation
│      │      │  │  └─rmi
│      │      │  ├─protocol
│      │      │  │  └─giopmsgheaders
│      │      │  ├─resolver
│      │      │  ├─transport
│      │      │  └─util
│      │      ├─internal
│      │      │  ├─corba
│      │      │  ├─CosNaming
│      │      │  ├─iiop
│      │      │  ├─Interceptors
│      │      │  └─POA
│      │      ├─org
│      │      │  └─omg
│      │      │      └─CORBA
│      │      ├─pept
│      │      │  ├─broker
│      │      │  ├─encoding
│      │      │  ├─protocol
│      │      │  └─transport
│      │      ├─PortableActivationIDL
│      │      │  ├─InitialNameServicePackage
│      │      │  ├─LocatorPackage
│      │      │  └─RepositoryPackage
│      │      └─spi
│      │          ├─activation
│      │          │  ├─InitialNameServicePackage
│      │          │  ├─LocatorPackage
│      │          │  └─RepositoryPackage
│      │          ├─copyobject
│      │          ├─encoding
│      │          ├─extension
│      │          ├─ior
│      │          │  └─iiop
│      │          ├─legacy
│      │          │  ├─connection
│      │          │  └─interceptor
│      │          ├─logging
│      │          ├─monitoring
│      │          ├─oa
│      │          ├─orb
│      │          ├─orbutil
│      │          │  ├─closure
│      │          │  ├─fsm
│      │          │  ├─proxy
│      │          │  └─threadpool
│      │          ├─presentation
│      │          │  └─rmi
│      │          ├─protocol
│      │          ├─resolver
│      │          ├─servicecontext
│      │          └─transport
│      ├─image
│      │  └─codec
│      │      └─jpeg
│      ├─imageio
│      │  ├─plugins
│      │  │  ├─bmp
│      │  │  ├─common
│      │  │  ├─gif
│      │  │  ├─jpeg
│      │  │  ├─png
│      │  │  └─wbmp
│      │  ├─spi
│      │  └─stream
│      ├─java
│      │  └─swing
│      │      └─plaf
│      │          ├─gtk
│      │          ├─motif
│      │          │  └─resources
│      │          ├─nimbus
│      │          └─windows
│      │              └─resources
│      ├─javadoc
│      ├─java_cup
│      │  └─internal
│      │      └─runtime
│      ├─jmx
│      │  ├─defaults
│      │  ├─interceptor
│      │  ├─mbeanserver
│      │  ├─remote
│      │  │  ├─internal
│      │  │  ├─protocol
│      │  │  │  ├─iiop
│      │  │  │  └─rmi
│      │  │  ├─security
│      │  │  └─util
│      │  └─snmp
│      │      ├─agent
│      │      ├─daemon
│      │      ├─defaults
│      │      ├─internal
│      │      ├─IPAcl
│      │      ├─mpm
│      │      └─tasks
│      ├─naming
│      │  └─internal
│      ├─org
│      │  └─apache
│      │      ├─bcel
│      │      │  └─internal
│      │      │      ├─classfile
│      │      │      ├─generic
│      │      │      └─util
│      │      ├─regexp
│      │      │  └─internal
│      │      ├─xalan
│      │      │  └─internal
│      │      │      ├─extensions
│      │      │      ├─lib
│      │      │      ├─res
│      │      │      ├─templates
│      │      │      ├─utils
│      │      │      ├─xslt
│      │      │      └─xsltc
│      │      │          ├─cmdline
│      │      │          │  └─getopt
│      │      │          ├─compiler
│      │      │          │  └─util
│      │      │          ├─dom
│      │      │          ├─runtime
│      │      │          │  └─output
│      │      │          ├─trax
│      │      │          └─util
│      │      ├─xerces
│      │      │  └─internal
│      │      │      ├─dom
│      │      │      │  └─events
│      │      │      ├─impl
│      │      │      │  ├─dtd
│      │      │      │  │  └─models
│      │      │      │  ├─dv
│      │      │      │  │  ├─dtd
│      │      │      │  │  ├─util
│      │      │      │  │  └─xs
│      │      │      │  ├─io
│      │      │      │  ├─msg
│      │      │      │  ├─validation
│      │      │      │  ├─xpath
│      │      │      │  │  └─regex
│      │      │      │  └─xs
│      │      │      │      ├─identity
│      │      │      │      ├─models
│      │      │      │      ├─opti
│      │      │      │      ├─traversers
│      │      │      │      └─util
│      │      │      ├─jaxp
│      │      │      │  ├─datatype
│      │      │      │  └─validation
│      │      │      ├─parsers
│      │      │      ├─util
│      │      │      ├─utils
│      │      │      ├─xinclude
│      │      │      ├─xni
│      │      │      │  ├─grammars
│      │      │      │  └─parser
│      │      │      ├─xpointer
│      │      │      └─xs
│      │      │          └─datatypes
│      │      ├─xml
│      │      │  └─internal
│      │      │      ├─dtm
│      │      │      │  └─ref
│      │      │      │      ├─dom2dtm
│      │      │      │      └─sax2dtm
│      │      │      ├─res
│      │      │      ├─resolver
│      │      │      │  ├─helpers
│      │      │      │  ├─readers
│      │      │      │  └─tools
│      │      │      ├─security
│      │      │      │  ├─algorithms
│      │      │      │  │  └─implementations
│      │      │      │  ├─c14n
│      │      │      │  │  ├─helper
│      │      │      │  │  └─implementations
│      │      │      │  ├─encryption
│      │      │      │  ├─exceptions
│      │      │      │  ├─keys
│      │      │      │  │  ├─content
│      │      │      │  │  │  ├─keyvalues
│      │      │      │  │  │  └─x509
│      │      │      │  │  ├─keyresolver
│      │      │      │  │  │  └─implementations
│      │      │      │  │  └─storage
│      │      │      │  │      └─implementations
│      │      │      │  ├─signature
│      │      │      │  │  └─reference
│      │      │      │  ├─transforms
│      │      │      │  │  ├─implementations
│      │      │      │  │  └─params
│      │      │      │  └─utils
│      │      │      │      └─resolver
│      │      │      │          └─implementations
│      │      │      ├─serialize
│      │      │      ├─serializer
│      │      │      │  └─utils
│      │      │      └─utils
│      │      │          └─res
│      │      └─xpath
│      │          └─internal
│      │              ├─axes
│      │              ├─compiler
│      │              ├─domapi
│      │              ├─functions
│      │              ├─jaxp
│      │              ├─objects
│      │              ├─operations
│      │              ├─patterns
│      │              └─res
│      ├─security
│      │  ├─auth
│      │  │  ├─callback
│      │  │  ├─login
│      │  │  └─module
│      │  └─jgss
│      └─source
│          ├─doctree
│          ├─tree
│          └─util
├─java  // JAVA 语言本身
│  ├─applet
│  ├─awt
│  │  ├─color
│  │  ├─datatransfer
│  │  ├─dnd
│  │  │  └─peer
│  │  ├─event
│  │  ├─font
│  │  ├─geom
│  │  ├─im
│  │  │  └─spi
│  │  ├─image
│  │  │  └─renderable
│  │  ├─peer
│  │  └─print
│  ├─beans
│  │  └─beancontext
│  ├─io
│  ├─lang
│  │  ├─annotation
│  │  ├─instrument
│  │  ├─invoke
│  │  ├─management
│  │  ├─ref
│  │  └─reflect
│  ├─math
│  ├─net
│  ├─nio
│  │  ├─channels
│  │  │  └─spi
│  │  ├─charset
│  │  │  └─spi
│  │  └─file
│  │      ├─attribute
│  │      └─spi
│  ├─rmi
│  │  ├─activation
│  │  ├─dgc
│  │  ├─registry
│  │  └─server
│  ├─security
│  │  ├─acl
│  │  ├─cert
│  │  ├─interfaces
│  │  └─spec
│  ├─sql
│  ├─text
│  │  └─spi
│  ├─time
│  │  ├─chrono
│  │  ├─format
│  │  ├─temporal
│  │  └─zone
│  └─util
│      ├─concurrent
│      │  ├─atomic
│      │  └─locks
│      ├─function
│      ├─jar
│      ├─logging
│      ├─prefs
│      ├─regex
│      ├─spi
│      ├─stream
│      └─zip
├─javax
│  ├─accessibility
│  ├─annotation
│  │  └─processing
│  ├─imageio
│  │  ├─event
│  │  ├─metadata
│  │  ├─plugins
│  │  │  ├─bmp
│  │  │  └─jpeg
│  │  ├─spi
│  │  └─stream
│  ├─lang
│  │  └─model
│  │      ├─element
│  │      ├─type
│  │      └─util
│  ├─management
│  │  ├─loading
│  │  ├─modelmbean
│  │  ├─monitor
│  │  ├─openmbean
│  │  ├─relation
│  │  ├─remote
│  │  │  └─rmi
│  │  └─timer
│  ├─naming
│  │  ├─directory
│  │  ├─event
│  │  ├─ldap
│  │  └─spi
│  ├─print
│  │  ├─attribute
│  │  │  └─standard
│  │  └─event
│  ├─rmi
│  │  ├─CORBA
│  │  └─ssl
│  ├─script
│  ├─security
│  │  ├─auth
│  │  │  ├─callback
│  │  │  ├─kerberos
│  │  │  ├─login
│  │  │  ├─spi
│  │  │  └─x500
│  │  ├─cert
│  │  └─sasl
│  ├─sound
│  │  ├─midi
│  │  │  └─spi
│  │  └─sampled
│  │      └─spi
│  ├─sql
│  │  └─rowset
│  │      ├─serial
│  │      └─spi
│  ├─swing
│  │  ├─border
│  │  ├─colorchooser
│  │  ├─event
│  │  ├─filechooser
│  │  ├─plaf
│  │  │  ├─basic
│  │  │  ├─metal
│  │  │  ├─multi
│  │  │  ├─nimbus
│  │  │  └─synth
│  │  ├─table
│  │  ├─text
│  │  │  ├─html
│  │  │  │  └─parser
│  │  │  └─rtf
│  │  ├─tree
│  │  └─undo
│  ├─tools
│  └─xml
│      ├─bind
│      │  ├─annotation
│      │  │  └─adapters
│      │  ├─attachment
│      │  ├─helpers
│      │  └─util
│      ├─crypto
│      │  ├─dom
│      │  └─dsig
│      │      ├─dom
│      │      ├─keyinfo
│      │      └─spec
│      ├─datatype
│      ├─namespace
│      ├─parsers
│      ├─soap
│      ├─stream
│      │  ├─events
│      │  └─util
│      ├─transform
│      │  ├─dom
│      │  ├─sax
│      │  ├─stax
│      │  └─stream
│      ├─validation
│      ├─ws
│      │  ├─handler
│      │  │  └─soap
│      │  ├─http
│      │  ├─soap
│      │  ├─spi
│      │  │  └─http
│      │  └─wsaddressing
│      └─xpath
├─launcher
└─org
    ├─ietf
    │  └─jgss
    ├─omg
    │  ├─CORBA
    │  │  ├─DynAnyPackage
    │  │  ├─ORBPackage
    │  │  ├─portable
    │  │  └─TypeCodePackage
    │  ├─CORBA_2_3
    │  │  └─portable
    │  ├─CosNaming
    │  │  ├─NamingContextExtPackage
    │  │  └─NamingContextPackage
    │  ├─Dynamic
    │  ├─DynamicAny
    │  │  ├─DynAnyFactoryPackage
    │  │  └─DynAnyPackage
    │  ├─IOP
    │  │  ├─CodecFactoryPackage
    │  │  └─CodecPackage
    │  ├─Messaging
    │  ├─PortableInterceptor
    │  │  └─ORBInitInfoPackage
    │  ├─PortableServer
    │  │  ├─CurrentPackage
    │  │  ├─POAManagerPackage
    │  │  ├─POAPackage
    │  │  ├─portable
    │  │  └─ServantLocatorPackage
    │  ├─SendingContext
    │  └─stub
    │      └─java
    │          └─rmi
    ├─w3c
    │  └─dom
    │      ├─bootstrap
    │      ├─css
    │      ├─events
    │      ├─html
    │      ├─ls
    │      ├─ranges
    │      ├─stylesheets
    │      ├─traversal
    │      ├─views
    │      └─xpath
    └─xml
        └─sax
            ├─ext
            └─helpers

```

