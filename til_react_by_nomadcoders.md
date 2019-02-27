## npm install react app with create-reactp-app by facebook
```sh
sudo npm install -g create-react-app
Password:
/usr/local/bin/create-react-app -> /usr/local/lib/node_modules/create-react-app/index.js
create-react-app@2.1.5 /usr/local/lib/node_modules/create-react-app
├── commander@2.18.0
├── semver@5.5.1
├── tmp@0.0.33 (os-tmpdir@1.0.2)
├── validate-npm-package-name@3.0.0 (builtins@1.0.3)
├── envinfo@5.11.1
├── cross-spawn@4.0.2 (which@1.3.1, lru-cache@4.1.5)
├── fs-extra@5.0.0 (universalify@0.1.2, jsonfile@4.0.0, graceful-fs@4.1.15)
├── chalk@1.1.3 (supports-color@2.0.0, escape-string-regexp@1.0.5, ansi-styles@2.2.1, strip-ansi@3.0.1, has-ansi@2.0.0)
├── tar-pack@3.4.1 (uid-number@0.0.6, once@1.4.0, debug@2.6.9, readable-stream@2.3.6, tar@2.2.1, fstream-ignore@1.0.5, rimraf@2.6.3, fstream@1.0.11)
└── hyperquest@2.1.3 (buffer-from@0.1.2, through2@0.6.5, duplexer2@0.0.2)
```

2가지 props , state 가 있다.
state 를 수정할때는 setState를 사용해야한다. 
-> component life cycle 을 이용하기위해 mutable 한 state 를 this.state에서 바로 수정하면 life cycle 이 움직이지 않는다.

Create : componentWillMount -> render -> componentDidMount 
Update : componentWillReceiveProps -> shouldComponentUpdate == true -> componentWillUpdate -> render -> componentDidUpdate 

로 진행된다. 

TODO : react 에 대해 til 해서 정리하도록 하자 md 스타일로도 작성해야함 까먹기 전에 적느라 적어둠. 
