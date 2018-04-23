#!/usr/bin/env node

const http = require('http');
const GitHub = require('github-api');
const prompt = require('prompt');
const git = require('nodegit');
const { spawnSync, spawn } = require('child_process');
const os = require('os');

const home = os.homedir();
process.chdir('/Users/ge_academy/repo/');

console.log("This file is " + __filename);
console.log("It's located in " + __dirname);

prompt.start();

prompt.get(['username','password'], function (err, { username, password }) {
	if (err) { return onErr(err); }

	console.log('Command-line input received:');

	const gh = new GitHub({
		username: 'vuyo97',
		password: '7Xhamfu!'
	});

	console.log({ gh });

	const user = gh.getUser();

	user.listRepos((err, repos) => { 
		repos.map((repo) => { 
			const ps = spawn('git', ['clone', repo.clone_url]);
			ps.stderr.on('data', (data) => {
				console.log(`grep stderr: ${data}`);
			});
			ps.stdout.on('data', (data) => {
				console.log(`grep stdout: ${data}`);
			});
		});

	});

});
