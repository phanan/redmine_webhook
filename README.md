Redmine WebHook Plugin
======================

A Redmine plugin posts webhook on creating and updating tickets.

Author
------------------------------
* @suer (original author)
* @phanan (rewriting and adding some features)

Install
------------------------------
Type below commands:

    $ cd $RAILS_ROOT/plugins
    $ git clone git@github.com:phanan/redmine_webhook.git
    $ rake redmine:plugins:migrate RAILS_ENV=production

Then, restart your redmine.

Post Data Example
------------------------------

### Issue opened

    {
      "payload": {
        "action": "opened",
        "issue": {
          "id": 1,
          "subject": "A sample bug",
          "description": "Lorem ipsum dolor sic amet.",
          "created_on": "2015-03-06T04:23:42Z",
          "updated_on": "2015-03-07T10:00:59Z",
          "closed_on": null,
          "root_id": 1,
          "parent_id": null,
          "done_ratio": 100,
          "start_date": "2015-03-02",
          "due_date": "2015-03-20",
          "estimated_hours": 15,
          "is_private": false,
          "lock_version": 14,
          "project": {
            "id": 1,
            "identifier": "playground",
            "name": "Playground",
            "description": "A sample playground project",
            "created_on": "2015-03-06T02:51:48Z",
            "homepage": ""
          },
          "status": {
            "id": 1,
            "name": "New"
          },
          "tracker": {
            "id": 2,
            "name": "Feature"
          },
          "priority": {
            "id": 3,
            "name": "High"
          },
          "author": {
            "id": 1,
            "login": "admin",
            "mail": "admin@example.net",
            "firstname": "Redmine",
            "lastname": "Admin",
            "identity_url": null,
            "icon_url": "http:\/\/www.gravatar.com\/avatar\/cb4f282fed12016bd18a879c1f27ff97?rating=PG&size=50"
          },
          "assignee": {
            "id": 5,
            "login": "demo",
            "mail": "me@phanan.net",
            "firstname": "Demo",
            "lastname": "User",
            "identity_url": null,
            "icon_url": "http:\/\/www.gravatar.com\/avatar\/0e5601057dfe4b0fa94611f1fad4fb95?rating=PG&size=50"
          },
          "watchers": [
            {
              "id": 1,
              "login": "admin",
              "mail": "admin@example.net",
              "firstname": "Redmine",
              "lastname": "Admin",
              "identity_url": null,
              "icon_url": "http:\/\/www.gravatar.com\/avatar\/cb4f282fed12016bd18a879c1f27ff97?rating=PG&size=50"
            }
          ]
        },
        "url": "http:\/\/localhost:3000\/issues\/1"
      }
    }

### Issue updated

    {
      "payload": {
        "action": "updated",
        "issue": {
          "id": 1,
          "subject": "A sample bug",
          "description": "Lorem ipsum dolor sic amet.",
          "created_on": "2015-03-06T04:23:42Z",
          "updated_on": "2015-03-07T10:00:59Z",
          "closed_on": null,
          "root_id": 1,
          "parent_id": null,
          "done_ratio": 100,
          "start_date": "2015-03-02",
          "due_date": "2015-03-20",
          "estimated_hours": 15,
          "is_private": false,
          "lock_version": 14,
          "project": {
            "id": 1,
            "identifier": "playground",
            "name": "Playground",
            "description": "A sample playground project",
            "created_on": "2015-03-06T02:51:48Z",
            "homepage": ""
          },
          "status": {
            "id": 2,
            "name": "In Progress"
          },
          "tracker": {
            "id": 2,
            "name": "Feature"
          },
          "priority": {
            "id": 2,
            "name": "Normal"
          },
          "author": {
            "id": 1,
            "login": "admin",
            "mail": "admin@example.net",
            "firstname": "Redmine",
            "lastname": "Admin",
            "identity_url": null,
            "icon_url": "http:\/\/www.gravatar.com\/avatar\/cb4f282fed12016bd18a879c1f27ff97?rating=PG&size=50"
          },
          "assignee": {
            "id": 5,
            "login": "demo",
            "mail": "me@phanan.net",
            "firstname": "Demo",
            "lastname": "User",
            "identity_url": null,
            "icon_url": "http:\/\/www.gravatar.com\/avatar\/0e5601057dfe4b0fa94611f1fad4fb95?rating=PG&size=50"
          },
          "watchers": [
            {
              "id": 1,
              "login": "admin",
              "mail": "admin@example.net",
              "firstname": "Redmine",
              "lastname": "Admin",
              "identity_url": null,
              "icon_url": "http:\/\/www.gravatar.com\/avatar\/cb4f282fed12016bd18a879c1f27ff97?rating=PG&size=50"
            }
          ]
        },
        "journal": {
          "id": 28,
          "notes": "",
          "created_on": "2015-03-07T10:00:59Z",
          "private_notes": false,
          "author": {
            "id": 1,
            "login": "admin",
            "mail": "admin@example.net",
            "firstname": "Redmine",
            "lastname": "Admin",
            "identity_url": null,
            "icon_url": "http:\/\/www.gravatar.com\/avatar\/cb4f282fed12016bd18a879c1f27ff97?rating=PG&size=50"
          },
          "details": [
            {
              "id": 56,
              "value": 3,
              "old_value": 1,
              "prop_key": "status_id",
              "property": "attr"
            },
            {
              "id": 57,
              "value": 3,
              "old_value": 2,
              "prop_key": "priority_id",
              "property": "attr"
            }
          ]
        },
        "journal_html": [
          "<strong>Status<\/strong> changed from <i>New<\/i> to <i>Resolved<\/i>",
          "<strong>Priority<\/strong> changed from <i>Normal<\/i> to <i>High<\/i>"
        ],
        "url": "http:\/\/localhost:3000\/issues\/1#change-28"
      }
    }

Requirements
------------------------------
* Redmine >= 2.4 (not tested with 3.x)

License
------------------------------
The MIT License (MIT)
Copyright (c) suer, [Phan An](http://phanan.net)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
