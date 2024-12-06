```
fj@github:~$ cargo run
```
```
hi! i'm fred (he/him) 👋
20 y/o aspiring developer from England, United Kingdom

check out my site @ https://freddysnow.com :)
```
```
fj@github:~$ cat src/main.rs
```
```rust
use chrono::{NaiveDate, TimeZone, Utc};

struct Human {
    name: String,
    pronouns: String,
    dob: NaiveDate,
    location: String,
    domain: String,
}

impl Human {
    fn calculate_age(&self) -> u32 {
        let today = Utc::now();
        today
            .years_since(Utc.from_utc_date(&self.dob).and_hms_opt(0, 0, 0).unwrap())
            .unwrap()
    }
}

fn main() {
    let fred = Human {
        name: "fred".to_string(),
        pronouns: "he/him".to_string(),
        dob: NaiveDate::from_ymd_opt(2004, 12, 03).unwrap(),
        location: "England, United Kingdom".to_string(),
        domain: "freddysnow.com".to_string(),
    };

    println!("hi! i'm {} ({}) 👋", fred.name, fred.pronouns);
    println!(
        "{} y/o aspiring developer from {}",
        fred.calculate_age(),
        fred.location
    );
    println!("\ncheck out my site @ https://{} :)", fred.domain);
}
```
