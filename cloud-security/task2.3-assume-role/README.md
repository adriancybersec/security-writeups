# TASK 2.3 – Did You Just Assume?

Wednesday, 4 Mar 2026

*Originally published on my UNSW OpenLearning blog.*

Is this method of granting access secure? (Justify your answers)

This method if done correctly is quite secure due to many security implementations, such as using least-privilege IAM permissions as well as temporary tokens and keys that automatically expire.

When the other person is assuming the role, temporary keys and tokens are created with an expiration date, ensuring these tokens can't be reused over long periods of time. This is a great security measure to avoid possible leaks of tokens and keys.

With AWS and how our accounts are managed, we are given barely any permissions, following the principle of least privilege. As I was doing 2.3, many things were restricted from me such as not being able to create a stack in certified regions. Moreover, I feel like some permissions that are restricted from my account need to be lifted in order for me to do some of the tasks.

Furthermore, passwords aren't being shared around which is a huge security measure. There are also detailed audit logs so you can trace potential attacks / unauthorized access attempts.

How can I prevent other people from using this role?

You can implement more measures such as MFA, secret conditions and you can even restrict the role so only a specific user can assume it. MFA is not implemented in the code given to us but could be implemented to ensure better security.

What I mean is say you want Bob to assume into your account, instead of giving the role permissions, you give Brian permissions if he has that role.

In the template given to us, one field says

 AWS: !Sub arn:aws:iam::${OtherAccount}:user/student

This means that only the student IAM user in the other account can assume.

Can other people use this role? If so, who are the people that can?

Based off the code, I don't think anyone else can assume as it only allows the student role to assume.

What is Cloudformation? How does it work? Why do/don’t we need this? What are the security risks that come with using this? If there are any security risks, how should we manage this?

Cloud formation is the service that allows us to write down AWS information in a file, typically YAML or JSON. Instead of manually adding roles / users we can write a file that automatically allows us to create resources. We were all given a yaml file named "comp3446-i-just-assumed-cf" which we used to create a new stack.

We need this for big infrastructure as it allows us to use the same infrastructure with ease, ensuring we don't have to do everything manually, improving efficiency. Also it helps us avoid human errors as it does it for us, improving consistency. The clean up is very easy to perform and takes little time, all we have to do is delete the stack.

We wouldn't need it if we had small infrastructure with only one role and bucket, it would be easier to manually create them.

Security risks that come with this include accidentally giving permission to everyone that has the role instead of giving it to specified users with the role. This is what we call misconfiguration within the trust policy as with wrong conditions unauthorized users could access and gain control.

We can manage this through ensuring there are no typos within the file, as well as using least privilege principal to ensure there is little damage if there was an attack.
